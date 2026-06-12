---
title: "Conky Refresh Text File Output"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by filam on 2008-03-08
I am currently displaying a text file (a todo list) with Conky. I was wondering if there is a way to refresh Conky so that it will display changes I make to the text file without restarting Conky. Is there any way to make it refresh the content of the file?
```
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes

use_spacer yes
use_xft no

update_interval 3.0

maximum_width 800 0

draw_shades no

draw_outline no
draw_borders no
draw_graph_borders no
uppercase no

stippled_borders 3

border_margin 9

border_width 10

default_color white

own_window_colour brown
own_window_transparent yes

alignment top_left

gap_x 10
gap_y 40

TEXT
${execi 3600 cat ~/ToDo }
```

---

### Post by RealPSL on 2008-03-08
Why not just set your execi parameter to 30 instead of 3600? I use conky to tail /var/log/messages at 30 intervals and it refreshes without a problem. The code is below

${execi 30 tail -n3 /var/log/messages | fold -w50}

---

