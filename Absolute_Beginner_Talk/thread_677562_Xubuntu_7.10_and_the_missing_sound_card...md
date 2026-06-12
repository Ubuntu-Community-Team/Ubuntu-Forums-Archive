---
title: "Xubuntu 7.10 and the missing sound card.."
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by OZFive on 2008-01-24
I have tried and tried and tried ti see if I can find a solution I can understand and do but I find myself up the proverbial creek without the paddle.  I have gotten my old Dell D300XT laptop to run Xubuntu pretty darn well and am really liking it, it started off "Just for work" and was not going to put anything special on it.  But then I started seeing how easy it was to use and using it more and more.  Now I want to go ahead and trick it out and play movies and music.  But the issue is that my sound card is not detected.  I have a cs4237b by Crystal semiconductor.  I have looked around and not seen any solutions that are understandable.  Is there any Ubuntu genius out there that can walk me though this easy?  Help please?

---

### Post by espressopigeon on 2008-01-25
Go to Menu->System->Restricted Drivers Manager. You may need to download a proprietary driver for your card to work.

---

### Post by mikeyphi on 2008-01-25
[http://www.linux.org/docs/ldp/howto/Alsa-sound-1.html](http://www.linux.org/docs/ldp/howto/Alsa-sound-1.html)

The above guide should sort your problem!
There's a lot to wade through - but you will find specifics for your chipset.

---

### Post by OZFive on 2008-01-25
I wil be trying this tonight and report back, keeping my fingers crossed, except when I am typing :P

---

### Post by OZFive on 2008-01-25
Ummm might I say that, those instructions look a bit daunting.  Does it come with a translation?  LOL

---

### Post by OZFive on 2008-01-29
I wish I could say I had great results but I seemed to have hosed the system and had to reinstall it all but of course am having the same issues.  I am very sad by this as I have a lot of songs on my iPod I want to listen to on my laptop while at work and resting/relaxing. 

I know this is a LOT to ask really, but there were so many instructions there, some specific to my system and I had a problem making sure I put the right ones in and then I also had a problem figurung out the right commands.  Is there anyone that can take some time out to help me a bit?  Maybe some step by step directions or walk me though it on a chat?  PLEASE?  Thanks

---

### Post by james_vanb on 2008-02-04
I'm using Xubuntu 7.10 on a Dell Latitude CP M233st containing the Crystal Audio cs4237b audio controller.  Took me the better part of a week to get the sound going.  If you looked at the Alsa Matrix, you may have found that the Cyrus Logic driver lists the cs4237b as working with the cs4236 driver.  If you've tried the Alsa guide, you probably have the updated drivers (Although I think they come with  the Xubuntu install).  Although I've gotten the sound to work, you'll have to redo the process when you reboot - I've just been Hibernating instead of shutting down.  Anywho....

You might want to reboot so that you're starting kind of fresh.

When you're ready, open a terminal and enter the following command:

cat /sys/devices/pnp0/00:0f/resources

You should get something like this:

state = active
io 0x210-0x217

The 0x210 is the cport number.  If your's is different, write it down, it's significant to the last command you're going to enter.

Now enter the following command:

cat /sys/devices/pnp0/00:10/resources

You should get something like this:

state = disabled
io 0x530-0x537
io 0x388-0x38b
io 0x220-0x22f
irq 5
dma 1
dma 0

The 0x530 is the port.  If your's is different, write it down.  You'll see why when we get to the final command.  Also note that the status is "Disabled".  This has to be activated for the sound card to work.  to activate, you have to have Super User privileges (Whatever that means).

To do that type the following command:

sudo -s

You'll be prompted to enter your password.

Now, to activate pnp0/00:10, use the following command:

echo activate > /sys/devices/pnp0/00:10/resources

This should activate the device. to check, type the following again:

cat /sys/devices/pnp0/00:10/resources

The status should now =Active.

Now that it's active, you need to load the driver.  Type the following:

sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

Note the port and cport numbers I mentioned above, If yours were different, modify the command appropriately (As well as the irq, dma1 and dma2).  If everything is the same as mine was - great.  

When you hit enter, you should hear your speakers "pop".  You now have sound.  Now enter the following:

alsamixer

when it opens, make sure nothing is muted (Keep the Mic muted as you'll just get feedback).  Put an audio cd in and mess with the levels until it sounds right.

As a final note, I installed mplayer and set that as default.  Totem just didn't work for me.

The following is a link to a great guide that helped me set things so I could listen to internet radio and view video, etc.  You have to install flash plugin and a bunch of codecs:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

If you shut down and need to get sound again, you only have to enter the following 3 commands:

sudo -s
echo activate > /sys/devices/pnp0/00:10/resources
sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

If anybody reads this and knows how to modify boot script to activate pnp0/00:10 on reboot, please post.

Good luck, hope this works for you.

To activate at start up:

sudo mousepad /etc/rc.local

Add the following after the last commented out line and before "exit=0":

echo activate > /sys/devices/pnp0/00:10/resources
sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

---

### Post by OZFive on 2008-02-05
I cannop wait to try this, I will be doing it this evening!  Thanks!

---

### Post by Kylian on 2008-03-04
It worked for me.
Thank's a lot for this rare clear tutorial.

Just a little remark:
> To activate at start up:

sudo mousepad /etc/rc.local

Add the following after the last commented out line and before "exit=0":

echo activate > /sys/devices/pnp0/00:10/resources
sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

"sudo" can be removed in rc.local since it's already executed in super user mode.

Thank's again.

---

### Post by james_vanb on 2008-03-05
Kylian

Glad it worked for you.  You're right, "sudo" not necessary in rc.local script.  That's what I get for copying and pasting commands.

---

