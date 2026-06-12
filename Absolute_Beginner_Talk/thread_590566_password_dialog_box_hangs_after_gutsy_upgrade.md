---
title: "password dialog box hangs after gutsy upgrade"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by arrrghhh on 2007-10-24
so far i have upgraded 3 machines to gutsy, and all went perfectly - except for my machine at home, which the upgrade was smooth but now whenever i get a GUI for 'enter you administrator password', the dialog hangs after i enter my password and press 'enter' or click 'ok' 

interesting to note, when i was running feisty & playing video on my second monitor, if the gui for admin password came up the video would freeze immediately until the dialog box went away.  now, when the dialog box comes up the video continues (slightly dimmer) and then it freezes right after i hit 'enter'.  i don't mistype the password at all, it always goes to whatever program it is going to - but it takes FOREVER to 'authenticate' or whatever the heck it is doing.  i'm guessing it's a hardware thing because my two work machines were both upgraded to gutsy and everything works perfectly.

also, i thought maybe a clean install would help.  so i wiped my hard drive and reinstalled gutsy clean - 64 bit, and same problem.  so i went back to 32 bit yesterday because i was having issues with flash.  now everything is great, but that password dialog box still hangs on me!  


i created a bug for it a the launchpad, but there has been no response... 

i was hoping to sort out this problem if i can, thanks!

[https://bugs.launchpad.net/bugs/152855](https://bugs.launchpad.net/bugs/152855)

---

### Post by snickers295 on 2007-10-25
upgrading to gusty seems to be buggy.
i would suggest a clean install.
maybe your CD is bad?
did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")?
maybe compiz fusion is messed up.
try googleing how to manually turn it off from the rescue mode.

---

### Post by arrrghhh on 2007-10-25
thanks for the reply.

i use xubuntu, so no compiz.

did an md5sum (every time, before i burn the disc and before i install the OS) - it was fine.

i have done a clean install... 2x.  this is #3 gutsy attempt on this machine.  1 upgrade from feisty 32 to gutsy 32.  then a clean gutsy 64.  and now a gutsy 32, still same issue.

i'm thinking it's hardware related because my 2 machines at work are fine...

thanks!

---

### Post by snickers295 on 2007-10-26
thats what it sounds like to me.
could you give me the list of hardware you have?

---

### Post by arrrghhh on 2007-10-26
> **snickers295 said:**
> thats what it sounds like to me.
could you give me the list of hardware you have?

certainly!  how silly of me.  should've done that in the first post.

Asus A8N_SLI Premium NForce4 motherboard (nvidia chipset, socket 939)
onboard lan & audio
AMD X2 4200+
NVIDIA GeForce 7600GT
1 gig of cosair ram (don't remember stats on that...)
120gb 3.0gb/s S-ATA drive for linux (swap, /home, /) (don't remember manufacuter... oops!)
2 additional hdd's for storage (200gb + 500gb)

i have a couple of pieces of hardware in there i don't use/couldn't get working... 1 is a cheapo tv capture card that worked horridly under windows, and i didn't invest much time with getting it working on linux.  also, i have a netgear PCI wifi card, which i also never went thru the steps to learn how to work.. if it even would, i just use the one of the ethernet ports that is onboard.  one is a nvidia and the other is marvell i want to say?  both integrated onto the mobo.

i should probably remove those two pieces of hardware, but i figure keep them in there so they don't get damaged.  i don't think i will ever use either, maybe the wifi card but not in the near future.  (note all this hardware was the same in feisty)

Thanks!

---

### Post by snickers295 on 2007-10-26
remove those pieces of hardware and then post back.

---

### Post by arrrghhh on 2007-10-27
sorry it took so long... but i removed both the capture card and the wifi card, no change.  as i stated in the bug report, after i open synaptic; type my root password and hit enter - i start a stopwatch.  from the time i hit enter to when the screen 'undimmed' was about 15.5 seconds.  if video would have been playing (which it wasn't, i tested after a fresh boot in without anything else running just to be sure) the video would have been stopped for 15.5 seconds, but the audio would continue.  very frustrating!

i appreciate any suggestions, thanks!

---

### Post by Threbus5 on 2007-10-27
Hi,

I feel your pain! Really.

I performed several installs of different carefully burned 7.10 Gutsy CDs with similar results. Upon install completion I would enter my user name and password - followed by a request to enter my user name and password followed by etc. Finally followed by reinstalling an earlier Ubuntu version. No, I did not have caps lock on either during the install or the post install restart. And Yes, I know my username and password. I kept the same ones through the upgrades.

So good luck. I intend to use the failed installs as justification to purchase a replacement, more feature laden laptop. Smile.

Take care.

---

### Post by arrrghhh on 2007-10-27
well that's not really the problem i'm experiencing...

actually the inital 'enter user/pass' screen is fine.  it's when i'm in the OS and it asks me for a password via the GUI password dialog.  the CLI is fine.  

and the problems you were experiencing threbus, that would make me NUTS!  so your installs wouldn't accept the password at all?  because that would be a very strange problem indeed....

---

### Post by Threbus5 on 2007-10-27
Well thanks for the condolences.

My old laptop behaves oddly. For example, the power charger has to be unplugged and then plugged back in just to turn the computer on. The network configuration tends to corrupt itself. Only as long as it remains "On" does it seem to work consistently. All of these pretty much negate the purpose of a laptop. Sigh.

So, one more oddity is just, well, one more oddity.

I wish you luck with your solution.

---

### Post by snickers295 on 2007-10-27
is it all the admin tasks or just one?

---

### Post by arrrghhh on 2007-10-29
sorry didn't see the reply... and for some reason my subscription to this thread did not let me know! at any rate...

ANY time the dialog box pops up (a GUI) asking for my admin password this occurs.  anything CLI is fine, but ANYTIME that dialog box pops up and asks for my root password, yes this happens.

and as i've noted before, the behavior of the dialog box is different from feisty... in feisty the video on my 2nd monitor would hang the second the dialog appeared.  now the dialog appears and the video doesn't hang until i hit "enter" or click "ok"

keep in mind i have tried this w/o anything else running (i know i keep referencing the video on my second monitor, i have tried this w/o any video playing, same result.)

thanks!

---

### Post by arrrghhh on 2007-11-01
so no one else has experienced this issue?  i guess not a lot of people use xubuntu...

---

### Post by jaybombalous on 2007-11-01
sounds like u should disable the second monitor and then get back with us!!

---

### Post by jaybombalous on 2007-11-01
I know when I need to do a gksudo command the desktop grays out. With a second monitor I can see this having some problems. Have u recently updated video drivers?

Seems to me the only logical piece of hardware it could be..

---

### Post by arrrghhh on 2007-11-19
didn't notice the replies here... after switching to kde i haven't had this issue.

it does seem like it would be video card related, another person was having issues and they switched from the nvidia-glx to the nv driver.  i couldn't get X to load with the nv driver, it would always crash.  and with the new 'unbreakable X' it would default to the vesa driver and i would just end up ctrl-alt-f1 and stop gdm and do the official nvidia installer - i had to do this every reboot!

haven't had that issue at all since the switch to kde... no gksu problems, no reinstallation of nvidia drivers every reboot... yea.

---

### Post by arrrghhh on 2007-11-20
after turning off 'compositing' the problem went away - entirely.  so it is DEFINITELY that package that is causing the gksu issues.

---

### Post by arrrghhh on 2007-11-23
evidently in addition to that, you can run "gksu-properties" and disable capture mode.

---

### Post by danny_ on 2008-01-29
> **arrrghhh said:**
> after turning off 'compositing' the problem went away - entirely.  so it is DEFINITELY that package that is causing the gksu issues.

I myself was having the same issues with Ubuntu 7.10, and Xfce 4.4.2 - and I turned compositing off and I no longer experienced the lag that was occurring.

Kudos.

---

