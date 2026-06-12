---
title: "Solution to Ubuntu 7.10 failure to load on G4"
date: 2008-02-03
forum: Apple PPC Users
---

### Post by Novalus on 2008-02-03
I used a G4 Titanium powerbook (TiBook) and installed Ubuntu 7.10

I had to use the 'alternate' install disk *NOT the live boot cd* to even start getting this OS onto my machine. as well its worth noting I have no experience with linux whatsoever. the internet helped me along, alot...
Alternate Installer iso: [http://cdimage.ubuntu.com/ports/releases/gutsy/release/ubuntu-7.10-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/gutsy/release/ubuntu-7.10-alternate-powerpc.iso)

This is for those of you that already got it installed but now it hangs at the loading screen or you get the busybox terminal:


'->' denotes a Return or "enter" keystroke

************************************* Loading Screen
((Are you stuck at a halted graphical loading screen?))
'Alt+Ctrl+F1'
************************************* BusyBox
((no? then your stuck at the busybox screen right?)) 
Then type this in:
'modprobe ide_core' ->
'exit' ->
************************************* Terminal
Ubuntu should now load! (but this is a temporary fix, we want it to do this everytime right? then read-on)
log into linux then run terminal and type:
'sudo vim /etc/initramfs-tools/modules' ->
<enter your password if prompted> ->
************************************* VIM
In the now opened VIM:
scroll to the bottom
Hit 'i' to insert text
move to the end of the current line (Left Arrow)
Enter to make a new line
Type 'ide-core' 
***
(note: some people have said 'ide_core' but my tibook g4 is on and I am looking at the line as I type this so I can't say if the dash or underscore make a difference)
***
Hit escape
Now type ':wq' (it should be appearing at the bottom of the window) then Enter to save and exit
************************************* Terminal
Back at the terminal now:
Type in 'sudo update-initramfs -u' ->

At this point I just rebooted my system, then got to watch the bar (as miscolored as it is on my screen), load itself past 1% and to the login screen.
*************************************
I hunted all over the internet to find various snippets and lengthy posts all of which were edited multiple times and progressively updated below themselves, some contradictory, and I figured -someone- could benefit from having it all in one place :D

As an extra note, those that want to be able to click by tapping the touchpad...
in terminal type:
'sudo trackpad tap' ->
to disable it again use:
'sudo trackpad notap' ->

Works: 
wifi, video

Not working still: 
sound, suspend/hibernate, left clicking option?, brightness adjustment

---

### Post by stream303 on 2008-02-04
Nice writeup - thanks for sharing!

If your powerbook is running an nvidia card, you may want to look at the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/21478](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/21478)

It got my usplash screen back in proper color and is reported by the bug-reporters to fix some brightness control problems in powerbooks

---

### Post by shawnhcorey on 2008-02-07
> **Novalus said:**
> I used a G4 Titanium powerbook (TiBook) and installed Ubuntu 7.10

I had to use the 'alternate' install disk *NOT the live boot cd* to even start getting this OS onto my machine.

Just the thought of using the alternative install scares the snot out of me.  Up to 6.10, the Live CD worked on Titaniums.  What is so different that it no longer works?  Why can't the software auto-detect the differences?  And why are us Titanium owners left so far behind?

---

### Post by Cows on 2008-02-19
This doesn't work for me.

Read my posts :

[http://ubuntuforums.org/showthread.php?p=4359959#post4359959](http://ubuntuforums.org/showthread.php?p=4359959#post4359959)

EDIT: Alright I fixed it. The problem was that I had "break=top" in my "append" section of /etc/yaboot.conf. It looks like break=top makes you go into a busybox. Also if you have "splash" in the "append" section then remove it if you are having problems with "video=ofonly" once you remove the splash you wont need "video=ofonly".

---

