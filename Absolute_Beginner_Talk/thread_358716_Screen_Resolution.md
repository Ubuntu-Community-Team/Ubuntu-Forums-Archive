---
title: "Screen Resolution"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Fribble on 2007-02-11
Hey folks,

I'm new to Ubuntu - and I mean new, as in, know nout at all about anything. So far it's been very impressive, though I'm still finding it difficult to use. That said, the only thing which has had me shouting at the screen so far has been the screen resolution. 

I only get the option to run in 1024 x 768. This wouldn't have been a problem ten years ago, but today, on an LCD screen, it's pretty nasty. I'd like to run in 1280 x 1024, but it won't let me.

Before you shout at me for not searching the forums for an answer, I already did. I have tried the following in Terminal, as per the advice in threads about similar problems:

sudo dpkg-reconfigure xserver-xorg

sudo gedit /etc/X11/xorg.conf

Neither works. They ask me for the root password, I enter the root password, it accepts the root password, but *nothing* happens. I re-enter the codes, and still nothing happens. I even rebooted and tried a second time, but nada. So I try to edit the xorg.conf manually, which seems easy enough, but it won't let me save the darned thing as it's read only. I try to change the permissions but it says I am not the owner, and there is no visible way of gaining root access to change them. 

So, any help here would be great, thanks! My eyes are glazing over!

---

### Post by laidback on 2007-02-11
To edit the file you need to use Sudo, e.g. :-  (Sudo invokes Super User i.e. root)

Sudo gedit /etc/X11/xorg.conf

You'll be asked for the password (which is your password) then Gedit will appear with the file ready for editting.

As a normal user you're not allowed to edit these system type files, which is a very good thing. I suggest you copy xorg.conf first.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old

if it's only a few minutes since you last entered your password you will not be asked for it again, otherwise you will.

I'm sorry but I'm unable to help you with your actual problem, I'm runnung 1280x1024 on an Acer AL1714 and understand your need, it's so much better especially since the screens are tailored to this resolution.

---

### Post by DenOK on 2007-02-11
> sudo dpkg-reconfigure xserver-xorg

I think that you should try to follow and answer all the questions that this will ask after that restart X server by ctrl+shift+bksp or just reboot.
Remember that when you run smth with sudo you should enter *your* password, not root's.
Also try googling on xorg.conf

Good Luck!

---

### Post by Fribble on 2007-02-11
Well thanks for trying to help folks, but I'm afraid it didn't work. The password I used didn't make any difference... for some reason, the relevant codes just had no effect whatsoever. The computer didn't even *try* to open them. It was as if the codes I was entering into the terminal weren't valid, but the computer seemed to accept them all the same.

So, in the end I had no choice but to reinstall. I'd only installed it today, and it only takes half an hour, so it wasn't like I lost a lot of stuff or took a lot of time. Once I'd finished the reinstall and put the new Nvidia drivers on again, I was still stuck in 1024x768 resolution... however this time, I was able to access the xorg.conf file via 'sudo gedit /etc/X11/xorg.conf' and change it properly. No problem this time. Very strange, all in all. And oddly enough, I had also lost a few options out of the System > Administration menu (important ones too, such as Users and Groups) for no apparent reason, which were restored to me upon a reinstall.

Nevertheless, I'm now posting to you in 1280x1024 resolution, so it's all good. Much prettier! Plus I managed to accidentally install my favourite game and it works fine, so I'm happy. Thanks again, you two!

---

### Post by nickoli_02 on 2007-02-11
Sounds like sudo wasn't accepting your password. Are you sure you were entering the password correctly? caps lock wasn't on?

---

### Post by Fribble on 2007-02-11
Oh, trust me, I entered the password so often that even if it wasn't the right one (which it was :D), the law of averages suggest that I should have gotten one right by accident, lol. I've used the very same password for this installation, and there are no problems. 

Besides, if I was entering the wrong password, the terminal would have told me as much. But it didn't - fresh command line, no error message, as though I hadn't typed anything in the first place. And subsequent command attempts didn't ask for a password, suggesting to me that it considered me to be 'logged in' already.

---

### Post by KAL9000 on 2007-02-11
I am going to add to this thread requesting information on what part of the file needs editing. I am trying to do this myself and following it do far...but when i open the xorg.conf file it is blank? What do I need to put in there or what should I see?

---

### Post by Fribble on 2007-02-11
You may need to create the configuration file after installing your drivers. 

For example, I have a nvidia card, and I had to type:

sudo nvidia-xconfig

...once the installation was completed to enable the files. All I had to do was reboot and try opening it again, and I no longer got a blank page.

That's just my experience though, sorry if that doesn't help you.

---

### Post by KAL9000 on 2007-02-11
The bank page seems to be some error. i get the blank page ONLY if sudo prompts for the pass word. if im within the "grace period" before the PW times out then if i try it works and shows me the file content, Its happend 3 times all the same. 

I did in the end just run through the long winded config setup thing thatruns the whole Xserver thing and enable the resolutions from there.

doesnt look like Im cutout for the Text editing config files quite yet :P

---

### Post by shareMenaPeace on 2007-02-11
On a sidenote you should choose 

> gksudo gedit as sudo gedit can crash because sudo dont support grafical editors.

You could also try text editor

> sudo nano -B /etc/X11/xorg.conf 
-B mackes a backup
And all stuff in linux is case sensitive.

---

