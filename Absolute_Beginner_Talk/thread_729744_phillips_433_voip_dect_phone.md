---
title: "phillips 433 voip dect phone"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2008-03-20
Recently I bought a Phillips unit as above very cheaply. It's actually a clear and long-range handset I am delighted to use. It has superb audio characteristics as a cordless phone.

'Can I use it with Skype?' was my question to the salesman.

'Yes, of course.' was his reply.

Well he was wrong but how does it work?

The 433 unit is pre-programmed for Windows Instant Messenger, which I guess is why Dick Smith was selling them for quarter price. ($30) I mean who uses WIM?

This is only for fun, but I like to learn.

Apparently these VOIP phones are recognised as alternative sound-card devices, so long as you don't try to make key-pad entries.

OK. With the Phillips 433 phone connected, it shows up as an alternative device in Skype>Options>Sound Devices. But it can't function as such so far.

I don't want to use its keypad function which I surmise is the WIM connection, but it would be handy to use it as a cordless phone when on Skype. Get my drift?

When connected to Skype, the handset is registered but won't or can't access input/output.

Is it possible to have a work-around so that the Phillips 433 phone can be utilised as a sound-card with Skype, ignoring WIM protocols re. keypad functions?

In other words; if Skype picks it up as an alternative sound device, disregarding keypad entries, why shouldn't it work?

Happy Easter to all, and cheers to all who've read my endlessly annoying  questions and taken them seriously.

Mike.

---

### Post by ohzopants on 2008-03-20
What are the permissions on the device?  This thing is USB right?

When I was trying to get my logitech usb headset working with skype I had to set the permissions of the device to the same as my sound card before skype could use it.

---

### Post by MichaelSM on 2008-03-20
Thanks ohzopants.

Yep it's a usb device and coincidentally I have a logitech usb headset too.

Could you explain the permissions issue? Is it in relation to System>Preferences>Sound?

Cheers,

Michael.

---

### Post by ohzopants on 2008-03-21
I'm on a windows computer right now... but I'll try to remember what I did off the top of my head.

First do:
```

lsusb

```

Now figure out which one is the phone.  Take note of the /dev/xxx that corresponds to it.

Do:
```

ls -l /dev/

```

Take a look at the owner and group of /dev/dsp (not 100% sure about dsp), which is your sound card.  In the same output find /dev/xxx (from lsusb) and check its owner and group.  If they do not match, WRITE DOWN WHAT THEY CURRENTLY ARE ON AN ACTUAL PIECE OF PAPER so that you can revert back if I'm wrong, change the owner and group like this:

```

sudo chown owner:group /dev/xxx

```

where 'owner' and 'group' are whatever values you had for /dev/dsp.  If I remember correctly the owner for my sound card is root and the group is 'audio'.

I hope this helps.

P.S.  I will be out of town all weekend, so I probably won't be back here before Monday.

---

### Post by MichaelSM on 2008-03-21
Here's lsusb, with the Phiips phone listed:


Bus 007 Device 002: ID 0471:0830 Philips 

I'm not sure what you mean about /dev/


Mike.

---

### Post by ohzopants on 2008-03-25
/dev/ is a directory that lists all the devices connected to your computer.  To be perfectly honest, most of /dev is a mystery to me.

One thing I do know, though, is that /dev/dsp is your soundcard.  If you do an 'ls -l' of /dev/dsp* it should come up with (at least):

crw-rw---- 1 root audio 14,  3 2008-03-16 20:10 /dev/dsp

This means that /dev/dsp (your soundcard) is owned by root and is accessible to all members of the 'audio' group.

I just busted out my logitech headset and noticed that it adds /dev/dsp1 with the same permissions as /dev/dsp so it should work without any fiddling.  The last time I tried it was 6.06 and back then it didn't do this. I don't have skype installed so I can't test it right now.

You should check if you get and new /dev/dspX when you plug in your phone.

I just did some quick googling and found this: [http://answers.yahoo.com/question/index?qid=20080325055906AA1UkOu](http://answers.yahoo.com/question/index?qid=20080325055906AA1UkOu)

You might not like it though.

---

### Post by MichaelSM on 2008-03-25
I appreciate your advice!

ls -l /dev/dsp* indicated four sound cards.

This is the Philips phone:

crw-rw---- 1 root audio 14, 19 2008-03-26 11:12 /dev/dsp1

The other units have the same permissions as this one.

It's all Greek to me!

Mike.

---

### Post by ohzopants on 2008-03-26
What sound devices does skype recognize?  What are the other 3?

---

### Post by MichaelSM on 2008-03-28
Thanks as always for the follow-up.

The three other devices are in order:

SB Live! sound card (six options too complicated to post)I just use it for PC speaker notifications of calls.
VIA onboard device (not disabled in BIOS....why? Dunno how)
Logitech usb headset (two options)

OK I hope this following helps:

Settings available for Philips and Logitech in Options>Sound Devices in Skype.

Philips VOIP433(hw:VOIP433.o)
Philips VOIP433(plughw:433.o)    and

Logitech USB Headset (hw.Headset,o)
Logitech USB Headset(plughw.o)

The settings I use for my Audio in/out are Logitech (hw.Headset.o) which work well.

The 'plugw' stuff means nothing to me. Is that a major issue?

Having learnt the value of accuracy I notice that the Philips hw: is followed by a colon, and the Logitech hw. is a full stop. 

Your time has been greatly appreciated.

Hope you can assist further.

Don't waste a nice weekend bothering with my silly issue! If something turns up, cool.

Thanks again,

Michael.

---

### Post by MichaelSM on 2008-03-28
Reply to my own post! Bad scene ...

Just so you know; one of the prerequisites for the Philips 433 is IE6 which I have installed but is not of course my default browser(the Philips phone doesn't require it to be default anyway, but at least it's there)

I don't use IE anything even on my XP VirtualBox, it's all Firefox.

Who on Earth uses Windows Instant Messenger anyway?

At worst the Philips phone is a superb dect cordless which retailed at $169 and they were throwing them out for $35. 

So I ain't complaining. It would have been fun to cobble it up not as a keypad but as a sound card for Skype.

Mike.

---

### Post by helliewm on 2008-06-18
I am having similar issues I want to be able to answer calls with the Phillips I am happy to make them through the keypad SKYPE SOFTWARE so just want to use it as a sound card. Although SKYPE detects it the phone does not ring.

Any ideas???

Helen

---

