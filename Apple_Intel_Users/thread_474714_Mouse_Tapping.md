---
title: "Mouse Tapping"
date: 2007-06-15
forum: Apple Intel Users
---

### Post by miyumi on 2007-06-15
Is there any way to stop the mouse from the random taps, highlighting, and dragging? That was what messed up Ubuntu the last time I had tried it. I know on my old computer it thought the touchpad mouse was an external mouse, but I don't remember how I found that out... or much of anything useful from my short attempt at using Ubuntu last summer.

---

### Post by miyumi on 2007-06-16
Or, if you could just tell me how to turn off the touch pad and only use the external mouse that I found today, that would be great too.

---

### Post by idn on 2007-06-16
This is something of great annoyance to be too! I accidently touch the touchpad when i am typing sometimes and the cursor gets sent to a random place in the document. I think but am not certain it involves editing the xorg.conf file, although you should probably seek advise from someone more knowledgable than myself before you touch it as playing with xorg.conf can causd havoc if not done properly from my own experience :)

---

### Post by floke on 2007-06-16
You can change the touchpad configurations, or even turn it off, with ksynaptics - I think there's a gsynaptics version too - they're in the repos.
Personally I hate ksynaptics - but if you want to turn off tapping etc, then its the way to go.

One thing though; you might have to enable shared memory by editing your xorg.conf file - if you get a message saying to need to set up 'SHMem' or whatever - then just add what the message says to your touchpad section in the xorg.conf file and restart x.

---

### Post by miyumi on 2007-06-16
How do I get there please?

---

### Post by floke on 2007-06-16
sudo apt-get install ksynaptics

(for KDE) - for gnome it would be gsynaptics - do a search in synaptic for it.

---

### Post by miyumi on 2007-06-16
I got it... how do I get into it?

---

### Post by floke on 2007-06-16
If you're in KDE then ALT+F2 = app launcher - just type ksynaptics into it
In gnome - try 'ksynaptics' from the terminal.

---

### Post by miyumi on 2007-06-16
... please bear with me, I really am trying these things before I ask you how to do them, it's just been a really long time.

I'm using gnome, and it tells me I need to edit xorg.conf or XF86Config, and I can't figure out how to open either of them in order to edit. I can't even find them to open them...

---

### Post by floke on 2007-06-16
That's quite alright ;)

To edit xorg...

First MAKE BACKUP!!!! I always use the convention _backup[date] - so ...in the terminal type

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup160607 (or whatever today's date is)

Is anything goes wrong - to restore simply reverse the above - i.e

sudo cp /etc/X11/xorg,conf_backup160607 /etc/X11/xorg.conf

To edit - type sudo gedit /etc/X11/xorg.conf

This will open a text editor in a window for you - to save the file once you've edited it click the 'save' disc icon.

What are you having to edit for anyway - is it the shared memory thing?

---

### Post by miyumi on 2007-06-16
The original message was:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Which I was warned might happen.

---

### Post by miyumi on 2007-06-16
How do I restart x? Do I have to restart the computer?

---

### Post by floke on 2007-06-16
Lol! No, you're not in Windows land now. just hit ctrl-alt-del and you'll go back to the login screen with X restarted. You'll lost data in open apps though - so make sure anything you need is saved first.

Did you edit xorg with the SSH whatever?

---

### Post by miyumi on 2007-06-16
Yes I did, and restarted x, and have taken the tap off the touchpad. 

Thank you very much for your help. And don't worry, I've saved all this in my backup files in case I need it again (cause I'm lazy, and prefer searching my text files to search a forum =P).

Thank you again.

---

### Post by floke on 2007-06-16
Glad it all worked out :popcorn:

---

