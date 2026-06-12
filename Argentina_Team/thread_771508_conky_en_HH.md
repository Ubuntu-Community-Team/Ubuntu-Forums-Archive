---
title: "conky en HH"
date: 2008-04-27
forum: Argentina Team
---

### Post by sebaxxxtian on 2008-04-27
hola

instale HH y lo unico en lo q estoy teniendo problemas es con conky. cuando inicia me aparece bien conky pero despues desaparece apenas abro una ventana de firefox.

no uso compiz-fusion ni beryl. y antes de escribir el post probe algunas cosa q vi en topics anteriores

aca va mi conkyrc. gracias por la ayuda....

# Create own window instead of using desktop (required in nautilus)
own_window yes


own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 10

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color 888a74

own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 0

# stuff after 'TEXT' will be formatted on screen
TEXT
$color
${color 33ff00}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
${color 33ff00}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   
$cpubar
${cpugraph 000000 ff0000}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${color 33ff00}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color
${battery} ${acpitempf}F ${wireless_essid ath0}
${color 33ff00}NETWORK (${addr ath0}) ${hr 2}$color
Down: $color${downspeed ath0} k/s ${alignr}Up: ${upspeed ath0} k/s
${downspeedgraph ath0 25,140 000000 ff0000} ${alignr}${upspeedgraph ath0
25,140 000000 ffff00}$color
Total: ${totaldown ath0} ${alignr}Total: ${totalup ath0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

---

### Post by sajnox on 2008-04-27
Hola,

Ejecuta conky desde una consola y luego lanza firefox como lo harias normalmente. Cuando conky se caiga quedara un mensaje en la consola, a partir de ahi seguro que hay algo mas para ver.

Saludos

---

### Post by MeduZa on 2008-04-27
tu problema no es que conky se cae sino que queda atras del desktop
proba eso haciendo control alt tab (son compiz o beryl)

por otro lado para repararlo proba estas 3 configuraciones:

own_window_type override
si no te anda
own_window_type normal
o
own_window_type desktop (que es la que creo que tenes ahora)

ademas de eso agregale a tu config:
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

below es para que salga abajo de todas las demas ventanas, sticky para que aparezca en todas las caras del cubo o en caso de metacity en todos los desktop.
skip_taskbar es para que no aparezca en la barra de tareas y pager no me acuerdo ^_^

cuando apretas el boton de show desktop (o mostrar escritorio) seguramente te va a desaparecer, eso lo reparo con compiz no se me ocurre como hacerlo en metacity.

suerte

---

### Post by oktubrer on 2008-04-27
skip_pager es para que no salga en el pager (el que muestra los escritorios virtuales con las ventanas que hay en cada uno)
ya sé, soy groso

---

### Post by sebaxxxtian on 2008-04-28
gracias ya lo zafe, ahora queria meterle los parametros del amarok, pero veo q es medio un lio, mejor lo dejo para mañana.

---

### Post by MeduZa on 2008-04-28
> **oktubrer said:**
> skip_pager es para que no salga en el pager (el que muestra los escritorios virtuales con las ventanas que hay en cada uno)
ya sé, soy groso

ahora entiendo porque no lo se
porque no uso el pager xD
igual sos groso ojo!! :)

---

