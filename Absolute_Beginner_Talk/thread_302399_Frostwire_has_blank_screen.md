---
title: "Frostwire has blank screen"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by markpurcell on 2006-11-18
I am brand new to linux and am not able to get frostwire to work. I installed it using Automatix. When I run it from the terminal I get the following stuff:

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading FrostWire:
log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).
log4j:WARN Please initialize the log4j system properly.
/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring


Whatever does this mean? Help me please.
Edit/Delete Message

---

### Post by taurus on 2006-11-18
But does it start?

---

### Post by markpurcell on 2006-11-18
yes, it starts. But the window is blank. The tip of the day screen works fine though.

---

### Post by markpurcell on 2006-11-18
Oh yeah. I am using ubuntu 6.10 edgy. Thank you

---

### Post by arnieboy on 2006-11-18
> **markpurcell said:**
> I am brand new to linux and am not able to get frostwire to work. I installed it using Automatix. When I run it from the terminal I get the following stuff:

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading FrostWire:
log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).
log4j:WARN Please initialize the log4j system properly.
/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring


Whatever does this mean? Help me please.
Edit/Delete Message
restore the original "human" theme on ubuntu and try again. Half of the ubuntu themes are broken and often cause issues with non GTK apps

---

### Post by markpurcell on 2006-11-18
Thanks for the reply. I neglected to mention that I am running Beryl. Does that have to go in order to do ftp?

---

### Post by arnieboy on 2006-11-18
> **markpurcell said:**
> Thanks for the reply. I neglected to mention that I am running Beryl. Does that have to go in order to do ftp?

well its a beryl theme problem then. default back to the usual and it should be ok.

---

### Post by xpod on 2006-11-18
My frostwire`s like that too if im using beryl in edgy..

Works fine if you just use metacity.

---

### Post by markpurcell on 2006-11-18
Yep. That was it. I really appreciate the help.

Metacity huh?
I'll check it out cause I really like Beryl.
Thanks again, fellas.

---

### Post by jordanmthomas on 2006-11-18
```
export AWT_TOOLKIT=MToolkit
```
If you put that in ~/.bashrc and run frostwire from a terminal, you should be able to see even with beryl running.

Also, you should be able to set AWT_TOOLKIT=MToolkit globally so you could just click the launcher, but I'm not 100% sure how to do that, and I wouldn't want to give bad information


You can read more about the bug here.

[http://www.google.com/search?hl=en&q=fix+swing+apps+beryl+compiz+export&btnG=Google+Search](http://www.google.com/search?hl=en&q=fix+swing+apps+beryl+compiz+export&btnG=Google+Search)
^^first link,  came across it when my GUI would never show up when I was doing my program for class.


**edit**
If you're feeling frisky, here's how I *think* you would go about adding it globally
```
sudo nano /etc/environment
```
add this line in there:
```
AWT_TOOLKIT="MToolkit"
```

---

### Post by glennric on 2006-11-19
This didn't work for me.  I can run Frostwire with metacity, but with Beryl it won't start.  I set the AWT_TOOLKIT environment variable, and when I start frostwire the splash screen appears and then the program just stops.  In the terminal I get similar errors to those that arnieboy got.  Setting the AWT_TOOLKIT did make it so that the Novell Groupwise client would work.  I was getting the same blank window with both that and Frostwire before.

Edit:  Actually I discovered that Frostwire also will not run in Metacity if AWT_TOOLKIT="MToolkit" is set.  I get the splash screen and errors from the terminal.  Then it stops.

---

### Post by xpod on 2006-11-19
Mabey im just not tooo fussy but Frostwire runs fine now for me in both Dapper and Edgy and it`s really no big deal just to use Metacity if your 
doing a bit of pilfering;) 

I try not to let some things bother me as it`s enough sussing out the stuff that does bother me.

Good luck regardles

---

### Post by glennric on 2006-11-19
> **xpod said:**
> Mabey im just not tooo fussy but Frostwire runs fine now for me in both Dapper and Edgy and it`s really no big deal just to use Metacity if your 
doing a bit of pilfering;) 

I try not to let some things bother me as it`s enough sussing out the stuff that does bother me.

Good luck regardles

To be honest I don't even intend to run Beryl on a regular basis.  I just like toying with things and seeing what I can get to work.  Beryl is eye candy, and that is about it.  I don't see why anyone who is concerned with functionality would run Beryl or Compiz.

---

### Post by mrgnash on 2006-11-26
> **glennric said:**
> To be honest I don't even intend to run Beryl on a regular basis.  I just like toying with things and seeing what I can get to work.  Beryl is eye candy, and that is about it.  I don't see why anyone who is concerned with functionality would run Beryl or Compiz.

Transparency comes in handy when working with windows on top of one another, such as a terminal and web-browser for instance; and the zoom/destkop switching stuff is very handy as well. 

Now that I'm used to Beryl/Compiz, I find regular metacity to be a very clunky interface.

---

### Post by Cardmaster91 on 2006-11-26
try this thread, it solved my frostwire problems, its the new beta 4.13.1

[http://ubuntuforums.org/showthread.php?t=305337]("http://ubuntuforums.org/showthread.php?t=305337")

---

### Post by gubatron on 2006-11-27
[Please upgrade to 4.13.1]("http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb")


Info on what's new and how to install here:
[http://www.frostwire.com/blog/2006/11/21/try-frostwire-413-ubuntu-installer-now-with-bittorrent/](http://www.frostwire.com/blog/2006/11/21/try-frostwire-413-ubuntu-installer-now-with-bittorrent/)

---

### Post by gundumfx on 2007-09-08
> **Cardmaster91 said:**
> try this thread, it solved my frostwire problems, its the new beta 4.13.1

[http://ubuntuforums.org/showthread.php?t=305337]("http://ubuntuforums.org/showthread.php?t=305337")

i have tryed the link you gave me but i do not understand it does not want to work well is it because i am  using feisty fawn

---

