---
title: "No Audio with Google Video"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by amwil1024 on 2006-09-10
I can see Google videos but cannot hear them. Help please!
](*,)

Dapper Drake 6.06 LTS is my version?

---

### Post by Abstract on 2006-09-10
Can you hear other flash videos? 

Try this:

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd 
```

---

### Post by amwil1024 on 2006-09-10
> **Abstract said:**
> Can you hear other flash videos? 

Try this:

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd 
```

Thank-youfor your reply. I'm sorry to e such a burden but I'm soo new that when you say, "Try This" code, I'm not sure exacly what to do with it!:confused: 

Do I simply go to Terminal and type it in then hit enter?

---

### Post by Abstract on 2006-09-10
Oh okay, sorry. Go to Applications -> Accessories -> Terminal.

Paste in the first line, hit enter. Wait till it finishes the try it with the second line. Hopefully you can now have sound on google video/flash.

---

### Post by amwil1024 on 2006-09-10
OK, Thanks,I'll try doing it that way. Oh, and to answer you first queston, no, no other flash audio work either. I tried Linspire demojust now to test it and there was no sound, so I'll now proceed to completing your instructions!

---

### Post by amwil1024 on 2006-09-10
Nope, no sound, cut N pasted first line then enter, repeated for second line,  nothing happened, so I rebooted Ubuntu, and tried Google video once more. No sound, Thanks for trying though! I read that audio is an acknowledged short coming with Ubuntu but they are working on a fix for the next release. I sure hope they fix it!

I can't play web based radio either, which I do alot of.

Thanks Once More!

---

### Post by RobsterUK on 2006-09-10
When you say "nothing happened" what do you mean? did you get an error?

---

### Post by amwil1024 on 2006-09-10
After entering second line of code the prompt returned, that's all that happened, so I figured to reboot before trying the video once more.

---

### Post by amwil1024 on 2006-09-10
I did a search and found this, [http://www.ubuntuforums.org/showthread.php?t=89827&highlight=audio+flash](http://www.ubuntuforums.org/showthread.php?t=89827&highlight=audio+flash)

the only part I'm not sure of what to do is the prt about PHP Code, at that point do I simply enter into Terminal at prompt the following? 

FIREFOX_DSP="arts"  

Its talking about changing the code, Is that simply done by entering FIREFOX_DSP="arts" at the terminal prompt? Sory to be such a smeg! : )

PART TWO: I entered the first line of cde and got this message,
Reading package lists... Done
Building dependency tree... Done
Package flashplayer-mozilla is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  flashplugin-nonfree
E: Package flashplayer-mozilla has no installation candidate

What does it mean??

---

### Post by bakert on 2006-09-10
> **amwil1024 said:**
> I can see Google videos but cannot hear them. Help please!
](*,)

A lot of people have had success resolving this with [Automatix](http://www.getautomatix.com/).  It's a program that, "makes supercharging Ubuntu Linux as easy as point and click"  according to the quote from PC World on their website.

There are instructions on how to install it here:

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_with_Apt](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_with_Apt)

Hope that helps!

---

### Post by amwil1024 on 2006-09-10
> **bakert said:**
> A lot of people have had success resolving this with [Automatix](http://www.getautomatix.com/).  It's a program that, "makes supercharging Ubuntu Linux as easy as point and click"  according to the quote from PC World on their website.

There are instructions on how to install it here:

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_with_Apt](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_with_Apt)

Hope that helps!

I have it installed already but not sure what your saying I should do with it?

---

### Post by amwil1024 on 2006-09-10
I've opened Automatix and it shows a bunch of stuff to check x for installing! Should I click on evrything!! Help!

---

### Post by Arevos on 2006-09-10
Only if you want everything on the list! Presumably, you'll just want to click on the checkbox next to "Flashplayer", then click OK. When Automatix asks if you wish to restore your original sources.list, click OK.

---

### Post by amwil1024 on 2006-09-10
I clicked on anything that pertained to video or audio on Automatix plus anything that remotely mentioned Firefox, Automatix loaded it all, I rebooted the pc, retried google video, and still have no sound.

What else? What about that link I posted earlier about a possible fix but I got some sort of erroe message, anyone ready totackle that one?

I apologize for being so dim witted, heck, put a bra on me and color my hair blonde!

---

### Post by xpod on 2006-09-10
Automatix is great but when i first used it on my first Ubu install i HAD to use that code up there too.
But strangely when i RE-installed ubu last week and got Automatix onto it again i never had to use the code this time.

Good luck anyway

---

### Post by Blondie on 2006-09-10
> **amwil1024 said:**
> I did a search and found this, [http://www.ubuntuforums.org/showthread.php?t=89827&highlight=audio+flash](http://www.ubuntuforums.org/showthread.php?t=89827&highlight=audio+flash)

the only part I'm not sure of what to do is the prt about PHP Code, at that point do I simply enter into Terminal at prompt the following? 

FIREFOX_DSP="arts"  

Its talking about changing the code, Is that simply done by entering FIREFOX_DSP="arts" at the terminal prompt? Sory to be such a smeg! : )

No, that's a config file. Open a terminal and type.

```
sudo gedit /etc/firefox/firefoxrc
```

A window will pop up with like FIREFOX_DSP="none" on the second line. Change it to read FIREFOX_DSP="arts". Then exit and click save.

---

### Post by Blondie on 2006-09-10
Alternatively you could try this.

Install alsa-oss using Synaptic Package Manager or simply type in a terminal,

```
sudo aptitude install alsa-oss
```

Then change the line in the text file as above to read
FIREFOX_DSP="aoss"

---

