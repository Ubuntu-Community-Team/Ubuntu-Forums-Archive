---
title: "Problema Conky"
date: 2008-03-29
forum: Argentina Team
---

### Post by xpelaox on 2008-03-29
Hola gente tengo un problemilla con conky, a veces cuando booteo, aparece el conky como "Always on top" aunque la opcion esta deshabilitada.

Esto tiene Solucion? uso gnome, y lei que conky no anda de 10 con gnome


saludos

---

### Post by InsektO on 2008-03-29
> **xpelaox said:**
> Hola gente tengo un problemilla con conky, a veces cuando booteo, aparece el conky como "Always on top" aunque la opcion esta deshabilitada.

Esto tiene Solucion? uso gnome, y lei que conky no anda de 10 con gnome


saludos

Estás usando Compiz? Podrías postear el contenido de .conkyrc?

Saludos!

---

### Post by xpelaox on 2008-03-30
si uso compiz.

```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
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
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color green

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${color #42AE4A}Usage (Avg):${color #42AE4A} ${freq_dyn_g}Ghz ${color lightgrey}${cpu cpu0}% ${alignr}${color #42AE4A}${cpubar cpu0 5,80}
${color #42AE4A}Usage (Core 1):${color #42AE4A} ${freq_dyn_g cpu1}Ghz ${color lightgrey}${cpu cpu1}% ${alignr}${color #42AE4A}${cpubar cpu1 5,80}
${color #42AE4A}Usage (Core 2):${color #42AE4A} ${freq_dyn_g cpu2}Ghz ${color lightgrey}${cpu cpu2}% ${alignr}${color #42AE4A}${cpubar cpu2 5,80}
${color #42AE4A}Average
${cpugraph cpu0 42AE4A eeeeee}
${color #42AE4A}Core 1 $alignr Core 2
${color #42AE4A}${cpugraph cpu1 25,120 42AE4A eeeeee} ${color #42AE4A} $alignr${color #42AE4A}${cpugraph cpu2 25,120 42AE4A eeeeee}
${color #42AE4A}Processes:${color lightgrey} $processes ${color #42AE4A}Run:${color lightgrey} $running_processes ${color #42AE4A}CPU Temp:${color lightgrey} ${execi 1100 cat /proc/acpi/thermal_zone/THRM/temperature | grep 'temperature:' | sed -e 's/temperature: //'}
${color #42AE4A}Core 1 Temp: ${color lightgrey}${execi 8 sensors | grep -A 1 'Core0' | cut -c13-16 | sed '/^$/d'} C ${color #42AE4A}Core 2 Temp: ${color lightgrey}${execi 8 sensors | grep -A 1 'Core1' | cut -c13-16 | sed '/^$/d'}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
hdb3:  ${fs_free_perc /media/sda2}%   ${fs_bar 6 /media/sda2}

${color orange}NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1
25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
${color orange}Fernando Ludueña, All Rights Reserved ${hr 2}$color

```

Lo raro de mi problema es que pasa solo a veces, lo que hago ahora es dar ctrl+alt+backspace hasta que aparezca bien, pero NO DA xD

---

### Post by kaivalagi on 2008-03-30
You might get more help is you ask questions in english? My spanish is terrible... <- Disculpas si he ofendido a nadie, mi error

I'll go out on a limb here and try to guess what you are asking :)

Are you trying to make conky start at login, and are having trouble with it sitting above all other application on the desktop? If so it might be that you are running conky before gnome has initialised fully. A quick test run from a terminal window will confirm:

```
killall conky
conky &
```

After doing the above does conky work okay? If so, then add a simple sleep command in a script and call that script on login rather than conky directly. So the script might look like this:

```
#!/bin/sh
sleep 20
conky &
```

Make sure the script is executable and reference it in you sessions configuration...

Hope that helps

---

### Post by sajnox on 2008-03-30
Kaivalagi,

This is the Argentinean Team and it's intented for spanish speaking people, not everybody speaks english.

Thanks for your help and i will try to translate your post

---

### Post by kaivalagi on 2008-03-30
Apologies :oops: I didn't notice the discussion group, I'll know to check next time...how English do I look!

I hope I have helped anyway

Pido disculpas, la manera negligente de mí! (blame the google translator if this doesn't read well :) )

---

### Post by guisheca on 2008-03-30
A mi también me pasa eso y lo que hago es matarlo y ejecutarlo de vuelta, con eso se arregla. Lo que propone el amigo de habla inglesa es hacer un script en bash que retrase la ejecución de conky, voy a probar a ver que sucede.

---

### Post by xpelaox on 2008-03-30
> **kaivalagi said:**
> You might get more help is you ask questions in english? My spanish is terrible... <- Disculpas si he ofendido a nadie, mi error

I'll go out on a limb here and try to guess what you are asking :)

Are you trying to make conky start at login, and are having trouble with it sitting above all other application on the desktop? If so it might be that you are running conky before gnome has initialised fully. A quick test run from a terminal window will confirm:

```
killall conky
conky &
```

After doing the above does conky work okay? If so, then add a simple sleep command in a script and call that script on login rather than conky directly. So the script might look like this:

```
#!/bin/sh
sleep 20
conky &
```

Make sure the script is executable and reference it in you sessions configuration...

Hope that helps

Hey! That perfectly fixed my Problem, Thanks you a lot!!!!! :D

---

### Post by kaivalagi on 2008-03-30
Glad I could help :)

---

### Post by sajnox on 2008-03-30
> **kaivalagi said:**
> Apologies :oops: I didn't notice the discussion group, I'll know to check next time...how English do I look!

I hope I have helped anyway

Pido disculpas, la manera negligente de mí! (blame the google translator if this doesn't read well :) )

You have helped, don't worry and you' re welcome to post in the Argentinean forum whenever you want. If you can't do it in spanish someone will translate

---

### Post by guisheca on 2008-04-08
Te cuento que el script mencionado por el muchacho de habla inglesa funciona la perfección. Abrí un documento vacío y agregale las líneas que pone él
```
#!/bin/sh
sleep 20
conky &
```
Guardalo con algún nombre que se te ocurra, por ejemplo conkyinicio.
Hacele un click derecho y andá a permisos, ponele que se pueda ejecutar como un programa. Listo, configurado el scrip.
Ahora vamos a Sistemas>preferencias>sesiones y donde lo teníamos al conky lo editamos poniendo la ruta del scrip que acabamos de crear.
Funciona perfecto, también lo implementé para gnome-do
Un saldudo, espero que no hayas desaparecido.

---

