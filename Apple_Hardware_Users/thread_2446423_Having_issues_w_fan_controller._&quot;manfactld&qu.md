---
title: "Having issues w/ fan controller. &quot;manfactld&quot;"
date: 2020-06-30
forum: Apple Hardware Users
---

### Post by gimchess on 2020-06-30
[SIZE=2](applogies in advanced if I'm missing something obvious )
My mac runs it's fans by defualt a little slower than it should so I downloaded "manfactld" and followed the instructions.

 [http://manpages.ubuntu.com/manpages/bionic/man1/macfanctld.1.html](http://manpages.ubuntu.com/manpages/bionic/man1/macfanctld.1.html)

I didn't run into any problems until I ran the command
[/SIZE]cat /etc/macfanctl.conf[SIZE=2]where I got to this in ther terminal.

[COLOR=#808080]cat /etc/macfanctl.conf
# Config file for macfanctl daemon
#
# Note: 0 < temp_X_floor < temp_X_ceiling
#       0 < fan_min < 6200       

fan_min: 2000

temp_avg_floor: 45
temp_avg_ceiling: 55

temp_TC0P_floor: 50
temp_TC0P_ceiling: 58

temp_TG0P_floor: 50
temp_TG0P_ceiling: 58

# Add sensors to be excluded here, separated by space, i.e.
# exclude: 1 7
# will disable reading of sensors temp1_input and temp7_input.

exclude:

# log_level values:
#   0: Startup / Exit logging only
#   1: Basic temp / fan logging
#   2: Log all sensors [/COLOR]

[/SIZE][COLOR=#000000][/COLOR][FONT=arial black][/FONT][FONT=arial][/FONT][SIZE=2][FONT=arial][COLOR=#000000]From here I'm confused on how to config these settings. Forexample when I ran  [/COLOR][COLOR=#696969]"fan min: 3000"[/COLOR][COLOR=#000000] i got
[/COLOR][COLOR=#808080]
Command 'fan' not found.[/COLOR][COLOR=#000000]

I tried to run "[/COLOR][COLOR=#696969]cat /etc/macfanctl.conf fan min:3000"
[/COLOR]...but got [COLOR=#000000]
[/COLOR][COLOR=#696969]cat: fan: No such file or directory
cat: 'min:3000': No such file or directory


[/COLOR]I'm lost on what to try, I just installed linux (lubuntu) for the first time yesterday but I won't be able to use it if I can't config the fans

thanks, josh[COLOR=#696969][/COLOR][COLOR=#000000]

[/COLOR][/FONT][/SIZE][COLOR=#000000][/COLOR]

---

### Post by &amp;KyT$0P# on 2020-06-30
[FONT=Courier New]/etc/macfanctl.conf[/FONT] is a text file you edit, not a guide to commands to run.

To edit it, use your favorite text editor with [FONT=Courier New]sudo[/FONT] (if your editor is a GUI program, use [FONT=Courier New]sudo -H[/FONT]).  Then run [FONT=Courier New]sudo systemctl restart macfanctld[/FONT] to apply the change without rebooting.

---

### Post by gimchess on 2020-06-30
Thanks! works like a charm. :D

---

### Post by &amp;KyT$0P# on 2020-06-30
You're welcome :KS

---

### Post by daniewicz on 2020-06-30
Another program that can be used to control Apple fan speeds is mbpfan. Make changes in /etc/mbpfan.conf

---

