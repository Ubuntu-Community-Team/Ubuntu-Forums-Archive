---
title: "[SOLVED] Dead down arrow and other Macbook keyboard woes"
date: 2008-11-05
forum: Apple Hardware Users
---

### Post by Rog-Mahal on 2008-11-05
I'm happily dual booting my Macbook 2,1 with OS X 10.4 and Ibex. However, I have a few keyboard issues:

1. My down arrow is dead. The other three work fine.

2. Keyboard LEDs do not function.

3. Backspace deletes text *incredibly* fast. 

4. Unable to map right click to the lower enter key.


I think I might have botched something, because I followed a few tips to tweak my keyboard. I inserted the text found [here in post #8]("http://http://ubuntuforums.org/showthread.php?t=960444"). I also attempted to use the method of mapping right click to the enter key found in the community docs, but it gave me an error:

```
$ sudo sed -i~ 's/KP_Enter/Pointer_Button3, Pointer_Button2/' /etc/X11/xkb/symbols/keypad
[sudo] password for roger: 
sed: can't read /etc/X11/xkb/symbols/keypad: No such file or directory
```

I had all these fixes running at the same time  on 8.04, but I guess something has gone awry. Any help would be appreciated, especially for that pesky down arrow.

---

### Post by cyberdork33 on 2008-11-05
> **Rog-Mahal said:**
> I'm happily dual booting my Macbook 2,1 with OS X 10.4 and Ibex. However, I have a few keyboard issues:

1. My down arrow is dead. The other three work fine.
There is another thread stating this too. Can you start a bug report?

> **Rog-Mahal said:**
> 2. Keyboard LEDs do not function.
The mouseemu package seems to interfere. remove it or just stop it.

> **Rog-Mahal said:**
> 3. Backspace deletes text *incredibly* fast. 
I have noticed that the keyboard repeat rate was increased a bit in Intrepid. The same thing will happen if you hold any key.

---

### Post by kosumi68 on 2008-11-05
> **Rog-Mahal said:**
> I'm happily dual booting my Macbook 2,1 with OS X 10.4 and Ibex. However, I have a few keyboard issues:

1. My down arrow is dead. The other three work fine.


If you have a custom xmodmap, I would suggest removing it, restarting and taking it from there.

> 
2. Keyboard LEDs do not function.


Sounds like you have the mouseemu package installed. Uninstall it - source of many problems.

> 
3. Backspace deletes text *incredibly* fast. 


Hum... new one - let's see if it persists after the two fixes above.

> 
4. Unable to map right click to the lower enter key.


With your machine and the appletouch kernel module, you should be able to get two-finger-and-click to work as a right click.

---

### Post by Rog-Mahal on 2008-11-06
I stopped using my custom xmodmap, and now Control works for the ctrl key and my down arrow problem was solved. Maybe I'll just keep it this way and not attempt to remap the command keys. 

Removing mouseemu restored LED function, but nearly gave me a heart attack because as soon as I removed it the whole keyboard went dead. I hard rebooted and now things are working fine, except now I have no right click. It was mapped to f12 natively by Ibex, but that no longer works. 

I'll search for a thread on how to do two finger+touch for right click, but I'd also like to figure out how to just map it to a key.


Because I think the problem with my dead down arrow was due to xmodmap, I'll hold off on filing a bug report. However, I still get those errors upon booting about being unable to activate the right keyboard configuration. It happened in Hardy also.

---

### Post by cyberdork33 on 2008-11-06
The mapping to F12 was a result of mouseemu (I know, I know), but there should be other ways of mapping right-click to a key.

There are several threads on setting up the touchpad to do a right click with a two-finger tap as well as doing a two-fingers-on-pad + click to get a right click as is possible under OS X. How to configure this properly has changed a bit in Intrepid, so be sure to check the the information is for Intrepid.

---

### Post by Rog-Mahal on 2008-11-07
Hmm, I've found plenty of posts about how to add 2 fingers+ click, but nothing about how to map right click to the lower enter key. I tried one version of the appletouch.fdi file to no avail, I have another one to try out when I reboot next. Is there a way to map it to that key? could I create the file that sed says doesn't exist? This new fdi system is a bit confusing to me...

---

### Post by Rog-Mahal on 2008-11-08
Marking as solved, I was unable to find a post related to mapping right click to a keyboard key in ibex, but I was able to get 2 finger tapping to work. Thanks for your help.

---

