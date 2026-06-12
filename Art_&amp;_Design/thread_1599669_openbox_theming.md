---
title: "openbox theming"
date: 2010-10-18
forum: Art &amp; Design
---

### Post by dzon65 on 2010-10-18
Hi.Anyone familiar with openbox theming? Here's the prob.Trying to get this theme wright but it keeps showing this "line" between the openbox theme and the gtk theme.It should be more fluent,not kinda split.The openbox gradient is set to 2C2C2C,the title seperator line is set to 2C2C2C as is the menubar's color.Don't get it.
Here's the rc.
# Window geometry
padding.width: 2
padding.height: 2
border.width: 1
window.client.padding.width: 0
window.client.padding.height: 0
window.handle.width: 2

#Menu geometry
menu.border.width: 0
menu.overlap: 0

# Border colors
window.active.border.color: #232323
window.inactive.border.color: #232323
menu.border.color: #232323
window.active.client.color: #525252
window.inactive.client.color: #525252

window.active.title.separator.color: #2C2C2C
window.inactive.title.separator.color: #2C2C2C

# Text shadows
window.active.label.text.font: shadow=y:shadowtint=70:shadowoffset=1
window.inactive.label.text.font: shadow=y:shadowtint=70:shadowoffset=1
menu.items.font: shadow=n
menu.title.text.font: shadow=y:shadowtint=70:shadowoffset=1

# Window title justification
window.label.text.justify: Center

# Active window
window.active.title.bg: flat Gradient Vertical
window.active.title.bg.color: #525252
window.active.title.bg.colorTo: #2C2C2C
window.active.title.bg.highlight: 82
window.active.title.bg.shadow: 10

window.active.label.bg: Parentrelative
window.active.label.text.color: #AAAAAA

window.active.handle.bg: flat Gradient Vertical
window.active.handle.bg.color: #2C2C2C
window.active.handle.bg.colorTo: #525252
window.active.handle.bg.highlight: 82
window.active.handle.bg.shadow: 16

window.active.grip.bg: flat Gradient Vertical
window.active.grip.bg.color: #2C2C2C
window.active.grip.bg.colorTo: #525252
window.inactive.grip.bg.highlight: 82
window.inactive.grip.bg.shadow: 16

window.active.button.unpressed.bg: parentrelative
window.active.button.unpressed.image.color: #00FFFF

window.active.button.pressed.bg: parentrelative
window.active.button.pressed.image.color: #FF8000

window.active.button.disabled.bg: parentrelative
window.active.button.disabled.image.color: #00FFFF

window.active.button.hover.bg: parentrelative
window.active.button.hover.image.color: #87FF07

window.active.button.toggled.unpressed.bg: parentrelative
window.active.button.toggled.unpressed.image.color: #00FFFF

window.active.button.toggled.pressed.bg: parentrelative
window.active.button.toggled.pressed.image.color: #FF8000

window.active.button.toggled.hover.bg: parentrelative
window.active.button.toggled.hover.image.color: #FF8000

# Inactive windows
window.inactive.title.bg: flat Gradient Vertical
window.inactive.title.bg.color: #525252
window.inactive.title.bg.colorTo: #2C2C2C
window.inactive.title.bg.highlight: 82
window.inactive.title.bg.shadow: 16

window.inactive.label.bg: Parentrelative
window.inactive.label.text.color: #BBBBBB

window.inactive.handle.bg: Raised Gradient Vertical
window.inactive.handle.bg.color: #171717
window.inactive.handle.bg.colorTo: #525252
window.inactive.handle.bg.highlight: 82
window.inactive.handle.bg.shadow: 16

window.inactive.grip.bg: Raised Gradient Vertical
window.inactive.grip.bg.color: #171717
window.inactive.grip.bg.colorTo: #525252
window.inactive.grip.bg.highlight: 82
window.inactive.grip.bg.shadow: 16

window.inactive.button.unpressed.bg: parentrelative
window.inactive.button.unpressed.image.color: #00FFFF

window.inactive.button.pressed.bg: parentrelative
window.inactive.button.pressed.image.color: #FF8000

window.inactive.button.disabled.bg: parentrelative
window.inactive.button.disabled.image.color: #00FFFF

window.inactive.button.hover.bg: parentrelative
window.inactive.button.hover.image.color: #87FF07

window.inactive.button.toggled.unpressed.bg: parentrelative
window.inactive.button.toggled.unpressed.image.color: #00FFFF

window.inactive.button.toggled.pressed.bg: parentrelative
window.inactive.button.toggled.pressed.image.color: #FF8000

window.inactive.button.toggled.hover.bg: parentrelative
window.inactive.button.toggled.hover.image.color: #FF8000

# Menus
menu.title.bg: Raised Gradient Vertical
menu.title.bg.color: #30343A
menu.title.bg.colorTo: #797D89
menu.title.text.color: #000000
menu.title.text.justify: Left

menu.separator.color: #202020
menu.separator.width: 1
menu.separator.padding.width: 6
menu.separator.padding.height: 3

menu.items.bg: sunken Bevel1 gradient Horizontal
menu.items.bg.color: #181818
menu.items.bg.colorTo: #2C2C2C
menu.items.text.color: #828282
menu.items.disabled.text.color: #aaaaaa

menu.items.active.bg: sunken gradient Vertical
menu.items.active.bg.color: #252525
menu.items.active.bg.colorTo: #393939
menu.items.active.text.color: #00FFFF
menu.items.active.disabled.text.color: #aaaaaa

#OSD
osd.bg: flat solid
osd.bg.color: #262626
osd.label.bg: parentrelative
osd.label.text.color: #909090
osd.hilight.bg: flat solid bevel1
osd.hilight.bg.color: #909090
osd.unhilight.bg: flat solid
osd.unhilight.bg.color: #373737

---

