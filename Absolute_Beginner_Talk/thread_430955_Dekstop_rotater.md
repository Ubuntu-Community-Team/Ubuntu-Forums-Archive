---
title: "Dekstop rotater?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-05-02
On windows i have a desktop rotater installed so i have a different image every 10 minutes or so.. is there something like this for ubuntu ?

---

### Post by starcraft.man on 2007-05-02
You might be looking for [this]("http://linuxappfinder.com/package/webilder") application, not certain.

---

### Post by LaurelLynn on 2007-05-02
Dear mech7,

Check out this page for a shell script example that changes the background randomly every hour.  But it has a link at the bottom to a crontab tutorial for changing the timing.

It could serve as a template for creating a more customized behavior.

[http://www.djlosch.com/article_Code:_Bash_Script_to_Change_Gnome_Background_Randomly_(Ubuntu](http://www.djlosch.com/article_Code:_Bash_Script_to_Change_Gnome_Background_Randomly_(Ubuntu))

---

### Post by mech7 on 2007-05-02
thanks but first one is for webimages it seems.. and second link the page is empty :(

---

### Post by starcraft.man on 2007-05-02
Grrrr, have to be registered... think you could paste the script here I'm interested? I would sign up but gah, makes me feel bad when I do that just for one thing. 

Have a heart for a nice, handsome zealot with cool beams coming out of his arms :p.

Edit: For mech, you have to sign up to view >.>.

---

### Post by LaurelLynn on 2007-05-02
Your right! That link only worked from the Google page. Here is the script:

```

#!/bin/bash
# script: change_backgrounds.sh - bash version
# version 2007.3.7
# description: randomly replace gnome background with one from a directory
# credits: David Loschiavo [http://www.djlosch.com], Steven Van Ingelgem
# license: GPL

bg_path=/mnt/archive/media/pics/backgrounds
extensions="jpg png gif jpeg JPG GIF PNG"
temp_bg_list=/tmp/bg_change_list

rm -f $temp_bg_list

for extension in $extensions
do
	find $bg_path -iregex ".*.$extension" >> "$temp_bg_list"
done

cnt=`wc -l "$temp_bg_list" | cut -f1 -d" "`
all_bgs=`echo \`expr $RANDOM % $cnt\``

selected_bg=`head -n$all_bgs "$temp_bg_list" | tail -n1`

logger "Changed desktop to: $selected_bg"

gconftool-2 -t string -s /desktop/gnome/background/picture_filename "$selected_bg"
exit 0

```

The last line before the exit shows the actual command to change the background.

Cron lets you  run a script at various intervals.  Basically the entries in "/etc/crontab" look like this

```
# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly

```
Note the columns "m h" for minutes and hours, others are "day of the month", "month", "day of the week". Everything after the user "root" is the command.    See the manpage from cron and crontab for more details.  That's just an example, don't run the script as root!

---

### Post by starcraft.man on 2007-05-02
Lots of thanks sweetie :D 

Saving it now, I'll work on it later today :)

*gives Laurel a hug*

Back to helping people, tweaking comes after supper.

---

### Post by imspecial on 2007-05-02
in synaptic search for wallpaper-tray or do ```
sudo apt-get install wallpaper-tray
```

to run the program you use the command wallpaper-tray but it should also place an icon in your graphics menu. To have the program run at start up place ```
wallpaper-tray
``` in your start up programs. Start up programs is located in System>preferences>sessions.

here is the home page of the program: [http://planetearthworm.com/projects/wp_tray/](http://planetearthworm.com/projects/wp_tray/)

---

### Post by mech7 on 2007-05-02
> **imspecial said:**
> in synaptic search for wallpaper-tray or do ```
sudo apt-get install wallpaper-tray
```

to run the program you use the command wallpaper-tray but it should also place an icon in your graphics menu. To have the program run at start up place ```
wallpaper-tray
``` in your start up programs. Start up programs is located in System>preferences>sessions.

here is the home page of the program: [http://planetearthworm.com/projects/wp_tray/](http://planetearthworm.com/projects/wp_tray/)

:guitar: Excellent exactly what i was looking for.

---

### Post by LaurelLynn on 2007-05-02
Hug you right back starcraft.man ;)

Glad you found what you were looking for mech7 :)

---

