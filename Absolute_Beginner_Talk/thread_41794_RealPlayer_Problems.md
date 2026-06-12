---
title: "RealPlayer Problems"
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by czambran on 2005-06-14
I tried installing realplayer the way described [http://www.ubuntuforums.org/showpost.php?p=13683&postcount=9](here) , and It appears it has been installed, it even appears on my Application menu, but when I click on the icon to launch it, nothing happens.

Is anybody having similar problems?

---

### Post by desdinova on 2005-06-14
test the install by using a terminal, and typing in it

realplay


what happens?

---

### Post by Xian on 2005-06-14
[QUOTE=czambran]I tried installing realplayer the way described [http://www.ubuntuforums.org/showpost.php?p=13683&postcount=9](here) , and It appears it has been installed, it even appears on my Application menu, but when I click on the icon to launch it, nothing happens.

Is anybody having similar problems?[/QUOTE]
Also, you might check and see if it is running "behind the scenes".
From the main panel goto:

Applications > System Tools > System Monitor.
Click on the "Processes" tab and scroll down the list.

Do you see a line that says 'realplay.bin'?

If so then you've probably got a sound conflict.
It can usually be fixed rather easily.

---

### Post by czambran on 2005-06-14
Same thing happens when I run it from the command line: Nothing(At least no window appears)

Here is a screenshot of System Monitor.

[IMG]http://www.turevista.org/Screenshot.png[/IMG]

---

### Post by Xian on 2005-06-14
Yeah, there's a sound conflict.
There's several ways to fix this.

1. Open a terminal and key in this command:
```
$ killall esd
```
2. Disable the sound server:

From the main panel goto System > Preferences > Sound
Untick the box "Enable Sound Server Startup"
Logout/Login

3. Open Synaptic and install the polypaudio package.

4. Follow the How-To at this [THREAD](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple).

I would do option 1 first to verify the problem and then option 4 to fix it.
Options 2 and 3 will also work but are a little more drastic.

---

### Post by czambran on 2005-06-14
yap it works now, but when I try to use a page with an embedded real player it still doesn't work, I think it might be because the port it uses is closed. How can I open a port in Ubuntu?

---

### Post by manicka on 2005-06-17
[QUOTE=Xian]Yeah, there's a sound conflict.
There's several ways to fix this.

1. Open a terminal and key in this command:
```
$ killall esd
```
2. Disable the sound server:

From the main panel goto System > Preferences > Sound
Untick the box "Enable Sound Server Startup"
Logout/Login

3. Open Synaptic and install the polypaudio package.

4. Follow the How-To at this [THREAD](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple).

I would do option 1 first to verify the problem and then option 4 to fix it.
Options 2 and 3 will also work but are a little more drastic.[/QUOTE]

Thanks for this Xian, nice to see you again on this forum. I wondered where you'd disappeared to :)

---

