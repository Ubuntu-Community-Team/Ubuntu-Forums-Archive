---
title: "Map keyboard keys to mouse buttons?"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Ansible on 2007-07-13
Is there a way to have keyboard keys execute mouse button clicks?  I'd like to map F2 and the numpad '+' key to the left click.  I use a trackball and I like to move the trackball with one hand and do the mouse clicks with the other hand.  The trackball alone makes my thumb tired.

---

### Post by mlissner on 2007-07-18
This should definitely be doable. Start by posting your xorg.conf file found - I believe - in /etc/Xorg.

From there *somebody* should be able to help you...that somebody won't be me though.

---

### Post by Likenota on 2007-07-21
[https://help.ubuntu.com/community/BluetoothSetup#head-bee296c661c86538ace528645fa6d5ff66ccaffc](https://help.ubuntu.com/community/BluetoothSetup#head-bee296c661c86538ace528645fa6d5ff66ccaffc)

yea i just installed the bluetooth and everything but hmm id like it so i can customize each button how would i go about doing this? is there a command list for the xorg.conf file or something for this ?....

---

### Post by Ansible on 2007-07-22
bluetooth?  for a bluetooth mouse?  what kind of bluetooth device do you mean?

I've come across a utility for mapping keyboard keys to console commands, an something else to change key mappings, but nothing that links the keyboard to the mouse buttons.  

There must be a way to do it though - how do people with macs simulate the right mouse button in ubuntu?  I haven't found anything on that yet.

---

### Post by Likenota on 2007-07-22
well just in general id like to get some of my media buttons and perhaps the lcd on my keyboard to be customized. ? the keyboard and mouse combo i have is MX5000 i found a .tar file that does all this but im totally clueless on how to make it work..

---

### Post by Ansible on 2007-08-02
bump

---

### Post by silverdancingcat on 2007-10-07
IMWheel will allow you to map a mouse click to one or more keyboard key presses, however I could not get it to 'hold down a key' while the mouse button is held down.

---

### Post by Ansible on 2007-10-19
Actually, what I want is the opposite - to map a keyboard key press to a mouse click.  So I can use a keyboard key instead of the mouse button.  It looks to me like IMWheel allows the opposite of what I want - to use a mouse button as a keyboard key.

I got this to work with a modified version of btnx, the only thing is the keypress still happens, so I get mouse down and key press at the same time.  I use F2 for this and F2 usually doesn't map to anything, but when it does its kind of a pain.

---

