---
title: "MacBook Pro Core Duo 2.16 15&quot; 1GB"
date: 2007-03-02
forum: Apple Intel Users
---

### Post by craigmarshall on 2007-03-02
I've just tried Ubuntu 6.10, the newest Ubuntu release as a live CD on my MacBook Pro. I would like to use only this operating system full time on my laptop, but it doesn't seem ready at present. I kept notes as I was trying it out, and I'll post those notes here for comment.

The Good:

* Used only 110MB of RAM
* Looks very nice (Antialiased fonts, "warm" theme, etc.)
* Includes most of my favourite apps (firefox, OO.o, GIMP), but also missing some others (Emacs, Inkscape).
* It detected my power cable being unplugged, and said something like "You're now running from battery power".

The Bad:

* My wireless didn't work. I went to System->Administration->Networking, and enabled the wifi controller, but there were no recognised networks, when there should have been.
* The screen resolution was 1024x768, and I didn't have an option to change it to 1440x900, which is my actual screen resolution.
* I couldn't see a way to right click or middle click. This could be handled by cmd-click and option-click, for example.
* I tried playing the sample audio file "Ubuntu sax.ogg", and the player loaded and looked like it was trying to play, but no sound came out. The volume was right up in the menu bar.
* I looked in System->Preferences->Power Management, and there didn't seem to be an option for sleep (suspend to ram), or hibernate (suspend to disk). 
* The hardware brightness controls didn't work (fn-F1 and fn-F2), nor any other fn-F* keys, e.g. mute, vol down, vol up, num lock, external screen chooser, keyboard light brightness.
* CD-eject didn't seem to work.
* The keyboard backlight didn't come on when I covered the ambient light sensors.

The Ugly:

I'm sure some people would call some of the above things ugly, but I'm not that harsh!


Are these problems in hand, or are there not enough developers that care about apple hardware, etc.? Is there a more apple/intel friendly distribution that I can try? Is the development version of Ubuntu taking care of these issues, or some of them?

The most important things to me that would need to work before I switch would be: wireless, screen, mouse, sound and cd-eject. I could probably live without sleep, hardware buttons and keyboard backlight if I had to! I am not whinging here, just trying to be as factual as possible. I would like to wait until these things work out of the box before I switch, I spend enough of my time playing with computers already. :-)

Thanks,
Craig Marshall

---

### Post by craigmarshall on 2007-03-02
Sorry to reply to myself. The other thing to add to the bad list, is as follows:

* Battery life shows as 1:36 only, with a fullish battery, it's around double that in Mac OS X.

This is not a critical problem, in other words, I could live with this, I just thought I'd complete my list.

Cheers,
Craig

---

### Post by craigmarshall on 2007-03-02
Untested Items include:

* iSight camera
* Built-in Microphone
* USB ports
* DVI port
* Firewire
* Ethernet
* Mini PCMCIA? (Not sure of name)
* Headphone socket
* Microphone socket (I think)

Cheers,
Craig

---

### Post by mustang on 2007-03-02
Yes, most of the problems you have described are common problems--some of which have been solved.

> * My wireless didn't work. I went to System->Administration->Networking, and enabled the wifi controller, but there were no recognised networks, when there should have been.

Go to madwifi.org and compile and install the latest drivers.

> 
* The screen resolution was 1024x768, and I didn't have an option to change it to 1440x900, which is my actual screen resolution.
* I couldn't see a way to right click or middle click. This could be handled by cmd-click and option-click, for example.
* The hardware brightness controls didn't work (fn-F1 and fn-F2), nor any other fn-F* keys, e.g. mute, vol down, vol up, num lock, external screen chooser, keyboard light brightness.


Go here: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

> 
* I looked in System->Preferences->Power Management, and there didn't seem to be an option for sleep (suspend to ram), or hibernate (suspend to disk).


Well hibernate is activated upon clicking "quit" and selecting hibernate. There won't be an option for that in power management. 

As far as sleep, that is the million dollar question right now. Even if you do have an option in power management (I do), there's a slim chance it will work. Read up on the other macbook threads as well as the mactel linux mail lists if you want any help on that as it is *very* tricky to get working (and from what I've read, even harder on the pro). 

Linux is still very rough around the edges on a macbook unfortunately. I am holding out for feisty and praying things work. If not, I'll probably be permanently booting osx.

---

### Post by craigmarshall on 2007-03-02
Thanks mustang for your quick reply.

I was hoping that I wouldn't need to compile anything, lets hope that a recent version of madwifi get rolled into Feisty then.

> Go here: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Same as above. Would rather not mess about with any settings out of the box if possible.

> Well hibernate is activated upon clicking "quit" and selecting hibernate. There won't be an option for that in power management. 

Ah - that is something I just didn't try. I was expecting something in the config to say shutdown, standby or hibernate when I close the lid on the computer. Nevermind, as I said before this is a want rather than a need (That's even if it works!).

> Linux is still very rough around the edges on a macbook unfortunately. I am holding out for feisty and praying things work. If not, I'll probably be permanently booting osx.

Yes - it's a shame, but I think the same applies to me. I don't have the time or energy to muck about with things. I was hoping it would just work. It says on the ubuntu.com desktop page, there is a strong focus on making it Just Work, I guess it's a goal that has just not been reached yet. I tried 5.10 or 6.04 before on this machine, and I did get a lot of stuff to work with a lot of fiddling, I just wanted to see how far it had come "out of the box". Not far enough for me yet. I'll check back in a month or two when Feisty is out (I assume it's April 07). For now, OS X is good enough.

Thanks for your time!
Craig

---

### Post by craigmarshall on 2007-03-03
Hello again. I've been playing with the latest testing CD Feisty 5 Desktop for x86, and it looks greatly improved, but still far from perfect. Here are the differences (and additions) to my original posts:

Hooray:

* The wireless worked immediately and intuitively
* Num lock works
* F3, F4 and F5 work for mute, vol down and vol up
* Eject worked

Boo:

* Machine seems louder and hotter than when running OS X and couldn't see a way to show or adjust fan speed or CPU temp.
* Some keyboard oddities. pressing £ (GBP) shows #, ` shows <, etc.
* Screen redrawing when moving windows is really slow for a supposedly reasonable gfx card.

The things that are currently blocking me from using (and possibly promoting or improving) Ubuntu Feisty out of the box, are:

* Screen resolution
* No sound
* No right click
* Machine is noisy and hot

I see that some people have managed to fiddle with their machines and get these problems fixed. I haven't had much luck though, I tried both 915resolution and fglrx, both with an X restart, and there was no improvement.

What are the chances of these things being ironed out for non-techy users before the Feisty release, or who could I speak to to find this out?

Thanks,
Craig Marshall

---

### Post by mustang on 2007-03-03
Craig,

thanks for taking the time to try out the new feisty build and posting your observation. One remedy you can use for the heat issues is to boot into osx and use an application called smcfancontrol to increase the minimum fan speed. Reboot into linux and this setting will carry over. It will not carry over a shutdown unfortunately.

Does suspend to ram work at all?

---

### Post by craigmarshall on 2007-03-06
Hi Mustang,

I do use smcfancontrol when in Mac OSX, but I didn't try to "carry over" the settings by rebooting to Ubuntu.

I haven't tried the suspending to ram yet either. I might have a go at both of these on the weekend.

Thanks,
Craig Marshall

---

### Post by shivathreya on 2007-03-17
The Bad:

* My wireless didn't work. I went to System->Administration->Networking, and enabled the wifi controller, but there were no recognised networks, when there should have been.

[B]You can use madwifi or ndiswrapper. Just install ndiswrapper (sudo apt-get install ndiswrapper)

Get the macbook winxp wifi driver and extract it. Go to the directory and type "sudo ndiswrapper -i net5211.inf". Then "sudo modprobe ndiswrapper". THen you should see ath0 in the command "ifconfig -a".

[/B]

* The screen resolution was 1024x768, and I didn't have an option to change it to 1440x900, which is my actual screen resolution.

**You have to install ATI drivers from [www.ati.com](www.ati.com). Then things should be OK**


* I couldn't see a way to right click or middle click. This could be handled by cmd-click and option-click, for example.

[B]Go to console and type
xmodmap -e "keycode 116 = Pointer_Button2"
xmodmap -e "keycode 108 = Pointer_Button3"
sudo apt-get install xkbset
xkbset m

Then you can use the Keypad Enter key for right click and the right Apple key for middleclick.

[/B]

* I tried playing the sample audio file "Ubuntu sax.ogg", and the player loaded and looked like it was trying to play, but no sound came out. The volume was right up in the menu bar.

**Open the mixer and go to "Switches". In that select "Line in as out" Then you will hear sound.**

* I looked in System->Preferences->Power Management, and there didn't seem to be an option for sleep (suspend to ram), or hibernate (suspend to disk).
* The hardware brightness controls didn't work (fn-F1 and fn-F2), nor any other fn-F* keys, e.g. mute, vol down, vol up, num lock, external screen chooser, keyboard light brightness.
* CD-eject didn't seem to work.
* The keyboard backlight didn't come on when I covered the ambient light sensors.

**For all these things you have compile mactel-patches into the kernel. See google. **

---

