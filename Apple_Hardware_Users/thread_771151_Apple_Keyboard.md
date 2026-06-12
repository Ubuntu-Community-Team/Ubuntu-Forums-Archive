---
title: "Apple Keyboard"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by Penguin Power on 2008-04-27
Hey, I can't get the shiny new Apple keyboard to play nicely with ubuntu. Depending on which keyset I use, I can disable the numpad enter key, the F keys, modifier keys etc... It doesn't seem that any of the many keyset options apply.

Has anyone managed to get the current generation Apple keyboard to work with ubuntu? Can I manually create a custom keyset? 

[[IMG]http://a248.e.akamai.net/7/248/8352/1058/store.apple.com/Catalog/uk/Images/MB110_lm.jpg[/IMG]High-res image of the keyboard.]("http://xs226.xs.to/xs226/08170/p1010057632.jpg")

---

### Post by cyberdork33 on 2008-04-27
there is a bug that has been triaged about these keyboards acting strangely.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887)

---

### Post by blurg on 2008-04-28
Hi

Mine works more or less but there are issues with the numpad - currently the kernel has been taught to recognise this as a laptop keyboard so if you hit the key below f16 all your letters disappear and uiop area turns into a numpad which sucks.

Hit f6 twice if that happened to you it should fix.

In keyboard prefs choose apple as vendor and mackintosh as the type and in the advanced options pay around with numpad options and you can get it more or less working normally.

I'm not writing this from Ubuntu so I can't check my exact setup just now - hopefully I've remembered correctly :)

---

### Post by Penguin Power on 2008-04-28
Thanks for the double-F6 tip, i can now use the Apple keyboard again :)

Even if it is still not quite the correct keyset...

---

### Post by Quillz on 2008-04-29
When you set up Ubuntu, you said that you had a Macintosh keyboard, right? Not sure if it makes any difference, but it certainly wouldn't hurt.

---

### Post by Kaziklu on 2008-04-29
I'm having the same issue, I can get the keyboard to behave like it were a laptop keyboard since 8.04 came out but that is it, 

On 7.10 everything worked out of the box, except f16, and the fn Key. Since I upgraded I'm having all sorts of odd issues.

---

### Post by McLeod Brennaman on 2008-04-29
Try using the 105-key standard PC map, with Meta mapped to your Cmd keys. Works for me, even the fn key. But Hardy's bizzarre, might not for you.

---

### Post by sands on 2008-04-30
I had a similar issue with a windows keyboard I connected to my macbook 3,1 SantaRosa
Both internal macbook keyboard and windows keyboard worked fine, when connected.. and when I remove the windows keyboard, macbook internal keyboard stops working..
and sometimes when I press alphabets on the macbook keyboard, numbers appear instead of alphabets.
In the login windows it worked fine.. After login the problem occurs.. This is how I fix it, when I get that problem..
 I delete the directory ~/.gconf/system/peripherals
logout and login

---

### Post by cyberdork33 on 2008-04-30
more related bugs:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/201711](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/201711)
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/214786](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/214786)

---

### Post by Penguin Power on 2008-05-03
Iam now getting this error dialogue every time x is started...

[IMG]http://xs227.xs.to/xs227/08180/screenshot895.png[/IMG]

Here are the outputs requested, anyone familiar with this error?

> sean@sean-desktop:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "gb", "gb", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "gb", "gb", ""

and...
> 
sean@sean-desktop:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = logiultrax
 overrideSettings = true
 options = []


---

### Post by Genotrius on 2008-05-03
I started a thread about this myself, without realizing that there was one. :P 
F6 fixed me up, but I have to wonder- How on Earth did you figure that out?

---

### Post by McLeod Brennaman on 2008-05-04
> **sands said:**
> I had a similar issue with a windows keyboard I connected to my macbook 3,1 SantaRosa
Both internal macbook keyboard and windows keyboard worked fine, when connected.. and when I remove the windows keyboard, macbook internal keyboard stops working..
and sometimes when I press alphabets on the macbook keyboard, numbers appear instead of alphabets.
In the login windows it worked fine.. After login the problem occurs.. This is how I fix it, when I get that problem..
 I delete the directory ~/.gconf/system/peripherals
logout and login

Sounds to me like when you hook up the PC keyboard, X switches to PC layout and keeps it there. The issue with the numbers instead of letters could be that numlock is stuck on, which would cause the characters JKLUIO to output as 123456 respectively; maybe try the F6 trick above.

Check out System->Preferences->Keyboard->Layout and see if it changes when you connect and disconnect the Win keyboard, if it does, just switch it back to Mac or pc105 (whichever is loaded before you connect the win keyboard). If it doesn't change, you got me, but it sounds like an X issue.



**RE: Penguin Power**
Your gconf and xprop outputs are almost correct, almost. Assuming you're using a notebook (MB or MBP), try this: run gconf-editor and in the left pane, open desktop->gnome->peripherals->keyboard->kbd right click that model entry and "Edit key..." to make it blank.

Assuming that doesn't work (it shouldn't alone), "sudo gedit /etc/X11/xorg.conf" and scroll down to the "InputDevice" with the identifier "Generic Keyboard" or "Configured Keyboard" or whatever it is for you. The driver should be "kbd" and it should have the following OPTIONs:

"CoreKeyboard"
"XkbRules"   "xorg"
"XkbModel"   "pc105"   *this can be macbook78, pc105, macintosh, and several others
"XkbLayout"  "us"

I use pc105 because it works better for me, but macbook78 sounds more native, so you may want to try that. If you have a lot more options or it doesn't seem to reflect this at all, you may want to just "sudo dpkg-reconfigure -phigh xserver-xorg" and blast your configuration. If you're still having issues after that, you're beyond me, and I apologize.

---

### Post by Penguin Power on 2008-05-05
> **McLeod Brennaman said:**
> Sounds to me like when you hook up the PC keyboard, X switches to PC layout and keeps it there. The issue with the numbers instead of letters could be that numlock is stuck on, which would cause the characters JKLUIO to output as 123456 respectively; maybe try the F6 trick above.

Check out System->Preferences->Keyboard->Layout and see if it changes when you connect and disconnect the Win keyboard, if it does, just switch it back to Mac or pc105 (whichever is loaded before you connect the win keyboard). If it doesn't change, you got me, but it sounds like an X issue.



**RE: Penguin Power**
Your gconf and xprop outputs are almost correct, almost. Assuming you're using a notebook (MB or MBP), try this: run gconf-editor and in the left pane, open desktop->gnome->peripherals->keyboard->kbd right click that model entry and "Edit key..." to make it blank.

Assuming that doesn't work (it shouldn't alone), "sudo gedit /etc/X11/xorg.conf" and scroll down to the "InputDevice" with the identifier "Generic Keyboard" or "Configured Keyboard" or whatever it is for you. The driver should be "kbd" and it should have the following OPTIONs:

"CoreKeyboard"
"XkbRules"   "xorg"
"XkbModel"   "pc105"   *this can be macbook78, pc105, macintosh, and several others
"XkbLayout"  "us"

I use pc105 because it works better for me, but macbook78 sounds more native, so you may want to try that. If you have a lot more options or it doesn't seem to reflect this at all, you may want to just "sudo dpkg-reconfigure -phigh xserver-xorg" and blast your configuration. If you're still having issues after that, you're beyond me, and I apologize.
Thanks for that, I'll try it out when I get on the desktop in question next time. It is a desktop however, and not a MB/MBP, just with Apple's USB keyboard.

---

### Post by roastbeef on 2008-05-05
I also have that keyboard - waiting for a fix for the num lock issue.

Also note - from 7.10 to 8.04 the function keys have changed.  You need to press 'Fn', followed by the function key (like on a mac) - for example, F2 is now Fn+F2.  I personally like it this way as I can now use the volume up/down keys as I would for a mac.  I believe you can change this by following the fixes outlined in the corresponding launchpad bug report pages.

---

### Post by sbeattie on 2008-09-25
Hi,

Would it be possible for some of the commenters to verify that the problem, as described originally in [https://bugs.launchpad.net/mactel-support/+bug/201887](https://bugs.launchpad.net/mactel-support/+bug/201887), is addressed by the kernel image in hardy-proposed? Please see [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) for documentation how to enable and use -proposed. I note that Justin Sunseri has appeared to do this already, so we're looking for one additional tester, though more would be better of course.

Thank you in advance!

---

