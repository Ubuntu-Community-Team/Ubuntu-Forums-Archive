---
title: "alsamixer: function snd_ctl_open failed for default: No such device"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by tonymoloney on 2008-03-02
I have searched the forums and Googled for a solution to this problem, but haven't found anything that works for me.
I have copied copious commands into the terminal and got just as many errors.
My system was working 100% until I tried to install VirtualBox. When VirtualBox wouldn't work, I removed it and then lost my sound.
I removed everything to do with ALSA and then re-installed all the ALSA stuff I could find without any success.
I'm running Kbuntu Gutsy on a Lenovo laptop and the soundcard identifies itself as 82801G
If I try to play an audio CD on a different desktop, I get a message saying that the audio output is busy and a list of xine parameters with nothing in it.
Anyone?

---

### Post by snkiz on 2008-03-02
Just a shot in the dark but could another program have grabed the sound card? you did try a reboot? I do know vbox is a bit of a pain to set up there is a kernel module that has to be enabled and you have to make a user group for it them make yourself a member of that group. my computer is a dinosouar and I got it working.. to slow to use though. hope that helps.

---

### Post by tonymoloney on 2008-03-02
One of the forum posts said that i had to be a member of the plugdev group, but I already was.
And yes, I rebooted after every change.

---

### Post by snkiz on 2008-03-03
That Doesn't Sound Right I Think Your Suposed to create a group called vbox users as for your sound card sorry i can't be any help that was all i had

---

### Post by PantherX on 2008-03-08
That's crazy.  I'm having the same issues... although I DID get VirtualBox to work... but now my sound card doesn't...

---

