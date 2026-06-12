---
title: "init.d script not working on reboot"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by orbeus on 2007-10-10
Hi

I have a script to start VLC that works fine from the terminal /etc/init.d/play but does not work when I reboot.

I have done   sudo update-rc.d play defaults    and   sudo chmod+x play

Also tried   sudo update-rc.d play start 51 S .

Any help greatly appreciated...

O

Ubuntu 7.04

---

### Post by aitorcalero on 2007-10-10
Why do you want to start VLC from /etc/init.d? Could not be used through sessions manager instead? :o
Maybe it does not work at reboot because VLC libraries needs X libraries. Script code will be also helpful to solve your problem ;)

---

### Post by orbeus on 2007-10-10
I'm trying to learn more about Linux so I wanted to see if I could get my computer to start playing music when I booted up. VLC seems the best to use.
As I mentioned this script works fine from terminal...

#!/bin/sh

play_start() {
echo "Starting play..." 
vlc --volume 400 --alsadev "hw:0,1" /usr/local/music &
}

play_stop() {
echo "Stopping play..."
killall vlc
}

play_restart() {
play_stop
sleep 1
play_start
}

case "$1" in
'start')
play_start
;;
'stop')
play_stop
;;
'restart')
play_restart
;;
*)
play_start
esac



TIA

O

---

### Post by orbeus on 2007-10-10
Played with Sessions and it does the trick...

Thanks for your help :)

O

---

### Post by Dr Small on 2007-10-10
export DISPLAY:0 probably would have did the trick too.

---

### Post by aitorcalero on 2007-10-10
This way seems too much complicated to me. But you can copy this script in your home directory with execution rights, and then call it through System / Preferences / Sessions / Startup Programs

I think that it does not work now because of the need of an X session for VLC to run

And also if you want you can also point to /usr/bin/vlc through the option commented before.

---

### Post by Dr Small on 2007-10-10
> **aitorcalero said:**
> This way seems too much complicated to me. But you can copy this script in your home directory with execution rights, and then call it through System / Preferences / Sessions / Startup Programs

I think that it does not work now because of the need of an X session for VLC to run

And also if you want you can also point to /usr/bin/vlc through the option commented before.
That is what the export DISPLAY:0 is about ;)

---

