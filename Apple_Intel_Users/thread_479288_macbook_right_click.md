---
title: "macbook right click"
date: 2007-06-20
forum: Apple Intel Users
---

### Post by dragonwings on 2007-06-20
how do i get my macbook  intel to right click 

iv heard that f12 is right but its not working for me

ubuntu 7.07 is the only os on it at the moment

please help sos sos

---

### Post by Laerte Andrade on 2007-06-20
I think that F12 works automagically if you install the package **pommed**:

```

sudo apt-get install pommed

```

You can also try some of the suggestions in this page:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by dragonwings on 2007-06-20
thank you for your reply but it didnt work  still have no right click at all

---

### Post by thonuz on 2007-06-20
3 finger tap on touchpad does a right click since feisty. What is wrong with that? using a keyboard shortcut takes more energy. Or add a 2 button mouse.

---

### Post by Torajima on 2007-06-20
> **dragonwings said:**
> thank you for your reply but it didnt work  still have no right click at all

Supposedly, with a little work you can enable two finger right clicking on the trackpad. I haven't been able to get it to work though.

What I did was map the right Apple key to right click. Unfortunately, I don't remember how I did it... but there should be a post in this forum telling you how to set it up.

---

### Post by ivesjd on 2007-06-20
Theres the code to do it.
```
#makes right cmd right click
xmodmap -e 'keycode 116 = Pointer_Button3'
``` Put this in /etc/rc.local and it will then run on boot.

---

### Post by dragonwings on 2007-06-22
three finger tap on mouse pad works great thank you for your help your a legend

---

### Post by Ken T on 2007-06-22
> **thonuz said:**
> 3 finger tap on touchpad does a right click since feisty.

I'm not sure whether you mean one finger tapped three times in quick succession, or three fingers tapped simultaneously on the pad, but I've tried both, and neither worked. (running feisty in vmware fusion beta 4). Any suggestions?


K.

---

### Post by ivesjd on 2007-06-22
If your running it in fusion, then it should be just like in OS X.

---

### Post by ~joe~ on 2007-06-23
> **ivesjd said:**
> If your running it in fusion, then it should be just like in OS X.
Yep, using an emulator means that you (usually) have to use the base operating system's conventions first. In Mac OS X, a right click can be simulated by holding down the Control key while clicking on something.

---

### Post by jcbwalsh on 2007-06-23
The only way I've gotten right click to work in 7.04 in VMWare Fusion is to set OS X to use two fingers on the trackpad and click as the right click. It's not a great solution, but as I said it's the only one I've found that works. 

In OS X
System Preferences -> Keyboard and Mouse -> Trackpad, then check "Place two fingers on trackad and click button for secondary click".

---

### Post by ivesjd on 2007-06-23
Personally I think that is a great way to implement right click. I prefer it to having a seperate mouse button. (It means less movement for right clicking). I belive that you can enable touch to tap right clicking, with two fingers... but then you would also have one finger left click.

---

### Post by 8daysaweek.co.uk on 2007-07-28
> **ivesjd said:**
> Theres the code to do it.
```
#makes right cmd right click
xmodmap -e 'keycode 116 = Pointer_Button3'
``` Put this in /etc/rc.local and it will then run on boot.

I tried this (and everything else in this thread, and on the ubuntu wiki) and nothing works for me except mouseemu - and then I lose the lights on num lock and caps lock, which I don't like.

I dislike tapping anyway so that was out.

I checked in the Package Manager that xmodmap was installed, then found that the above works if I type ```
sudo xmodmap -e 'keycode 116 = Pointer_Button3'
``` into the terminal, after which I am prompted for my password.

This makes me think that either[LIST=1]
[*]rc.local is not being run for some reason
[*]perhaps I need to preface the command with "sudo"
[*]or maybe it's an authentication problem?[/LIST]

This is the complete content of my rc.local file if that helps:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# make right cmd right click
xmodmap -e 'keycode 116 = Pointer_Button3'

exit 0
```
I'd really appreciate some help getting this running automatically.  In the meantime I'll keep trying things and post if I'm successful!

---

### Post by 8daysaweek.co.uk on 2007-07-28
OK, I have noticed that when I restart (Ctrl + Alt + Backspace) that after the rc.local line it briefly says```
xmodmap: unable to open display ''            [[COLOR="Red"]fail[/COLOR]]
``` before prompting me to log in.

Any ideas?  TIA :)

---

### Post by 8daysaweek.co.uk on 2007-07-28
OK, I think I've figured it out...

rc.local isn't executing for some reason, **if anyone can tell me why I'd love to know**.

In the end I followed the instructions here: [ Disable touchpad tapping while typing (that is sooo annoying)]("http://ubuntuforums.org/showthread.php?t=434625")
here: [Running Scripts Automatically]("http://www.kernow.pwp.blueyonder.co.uk/xwin/xset.html#scripts")
and here: [ HowTo: Disable Synaptics Touchpad While Typing]("http://ubuntuforums.org/showthread.php?t=271052") (to find out about the sessions manager: System -> Preferences -> Sessions)
and then I added the xmodmap command to the script I created for this.

...at least it seems to be working for now ;)

---

### Post by luisbg on 2007-07-29
Thanks to qsynaptics I have it so two finger tap does middle click, and three finger tap does right click. One finger tap is annoying so I have nothing there.

luisbg

---

### Post by fredscripts on 2008-02-17
I'm running Ubuntu 7.10 on a macbook. There's nowadays an easy way to get right click on that? how do I scroll down?

Thanks!

---

### Post by fredscripts on 2008-02-17
And by the way, any webside with keyboard tricks of ubuntu in a macbook? I mean how to simulate some keys that are not on the macbook keyboard? Delete?

Thanks!

---

### Post by phetre on 2008-02-17
This article should help you with right clicking and much more:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Good luck!

---

### Post by ichiniisan on 2008-03-14
since no one answered 8daysaweek.co.uk ill do this then...
the rc.local file says:
# In order to enable or disable this script just change the execution
# bits.

which tells you why it wont execute.  A simple search in google will give you the basics of any operating system. Users can read, write and execute files. permissions exist for such: owner, group and others. Simply change the permissions for the root user to be able to execute the file. To do this as the root user:
chmod +x rc.local

if it isnt executable it wont execute.

---

