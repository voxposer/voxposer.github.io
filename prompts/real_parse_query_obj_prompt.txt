import numpy as np
from perception_utils import detect

objects = ['table', 'gripper', 'green block', 'cardboard box']
# Query: gripper.
gripper = detect('gripper')[0]
ret_val = gripper

objects = ['table', 'gripper', 'drawer', 'egg', 'egg', 'plate']
# Query: topmost handle.
handles = detect('drawer handle')
handles = sorted(handles, key=lambda x: x.position[2])
top_handle = handles[-1]
ret_val = top_handle

objects = ['table', 'gripper', 'yellow block', 'charging cable', 'cyan block', 'magenta block']
# Query: second to the left block.
blocks = detect('block')
blocks = sorted(blocks, key=lambda x: x.position[1])
second_left_block = blocks[1]
ret_val = second_left_block

objects = ['table', 'gripper', 'iPhone', 'ruler', 'pink line', 'blue line']
# Query: the front most line on the table.
lines = detect('line')
lines = sorted(lines, key=lambda x: x.position[0])
front_most_line = lines[-1]
ret_val = front_most_line

objects = ['table', 'gripper', 'vase', 'napkin box', 'mask']
# Query: table.
table = detect('table')[0]
ret_val = table

objects = ['table', 'gripper', 'bottle', 'drawer', 'bowl', 'bag']
# Query: second to the bottom handle.
handles = detect('drawer handle')
handles = sorted(handles, key=lambda x: x.position[2])
second_bottom_handle = handles[1]
ret_val = second_bottom_handle

objects = ['table', 'gripper', 'brown line', 'red block', 'monitor']
# Query: brown line.
brown_line = detect('brown line')[0]
ret_val = brown_line

objects = ['table', 'gripper', 'green block', 'cup holder', 'black block']
# Query: block.
block = detect('green block')[0]
ret_val = block

objects = ['table', 'gripper', 'mouse', 'yellow bowl', 'brown bowl', 'sticker']
# Query: bowl closest to the sticker.
bowls = detect('bowl')
sticker = detect('sticker')[0]
closest_bowl = min(bowls, key=lambda x: np.linalg.norm(x.position - sticker.position))
ret_val = closest_bowl

objects = ['table', 'gripper', 'keyboard', 'brown bag', 'pink bag', 'red tape', 'bottle']
# Query: bag with the red tape on top.
bags = detect('bag')
red_tape = detect('red tape')[0]
bag_with_red_tape = min(bags, key=lambda x: np.linalg.norm(x.position - red_tape.position))
ret_val = bag_with_red_tape

objects = ['table', 'gripper', 'grape', 'wood tray', 'strawberry', 'white tray', 'blue tray', 'bread']
# Query: tray that contains the bread.
trays = detect('tray')
bread = detect('bread')[0]
tray_with_bread = min(trays, key=lambda x: np.linalg.norm(x.position - bread.position))
ret_val = tray_with_bread

objects = ['table', 'gripper', 'drawer']
# Query: top drawer handle.
handles = detect('drawer handle')
top_drawer_handle = max(handles, key=lambda x: x.position[2])
ret_val = top_drawer_handle

objects = ['table', 'gripper', 'door']
# Query: the thing you can open the door with.
door_handle = detect('door handle')[0]
ret_val = door_handle

objects = ['table', 'gripper', 'glass', 'vase', 'plastic bottle', 'block', 'phone case']
# Query: anything fragile.
fragile_items = []
for obj in ['glass', 'vase']:
    item = detect(obj)[0]
    fragile_items.append(item)
ret_val = fragile_items

objects = ['table', 'gripper', 'fridge']
# Query: fridge handle.
fridge_handle = detect('fridge handle')[0]
ret_val = fridge_handle

objects = ['table', 'gripper', 'blue block', 'red block']
# Query: green block.
ret_val = None

objects = ['table', 'gripper', 'yellow bowl', 'red spoon']
# Query: gripper.
gripper = detect('gripper')[0]
ret_val = gripper