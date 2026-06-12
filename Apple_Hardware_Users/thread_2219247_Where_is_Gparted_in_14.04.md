---
title: "Where is Gparted in 14.04?"
date: 2014-04-23
forum: Apple Hardware Users
---

### Post by este.el.paz on 2014-04-23
Folks:

Did a fresh install of Xubuntu 14.04 on the '10 MBPro last night . . . and all went well . . . got the wifi going and nvidia driver set up.  This AM I installed synaptic and gparted from Terminal . . . synaptic is showing up in the drop down menu, but gparted seems to be hiding.  I checked it in synaptic and it shows gparted is installed, I tried one of the launch app applications and gparted does not show up . . . actually in one of them it gave me a "gparted requires root privileges" error, but then . . . nothing--same thing in Terminal, I typed "gparted" and got the error notification, no gparted GUI.  I logged in and out several times and rebooted . . . nada.  Any thoughts on how to get my good buddy gparted to show its face?

Otherwise it seems like this latest iteration of Xubuntu is very nice . . . it might give LM a good run for its money . . . one difference, the ability to reboot from the Terminal . . . which due to "mdm" issues in LM16 was a bug-a-boo that was not going away . . . had to log out, then click restart which would go to a tty window, asking for password, then type "sudo reboot" . . . asking for another password . . . and only then would it restart . . . .  But, problem that I had hoped would be resolved is the dreaded "synaptics" bug that makes the cursor jump erratically while typing . . . be nice to have more function on the touchpad, as solution in LM was "disable tap to click" . . . .

Anyway, might try to add the Mate DE to this and see how that goes, but, for the meanwhile, any ideas as to where the console stuffed the install of GParted?

Many thanks,

eep

---

### Post by sudodus on 2014-04-23
***Gparted*** is usually only part of the install CD/DVD/USB drive, but you have to install it from the repositories to get it in an installed system.

---

### Post by Elfy on 2014-04-23
gparted hides in Settings Manager - has done for at least 2 releases that I'm aware of

---

### Post by este.el.paz on 2014-04-23
> **Elfy said:**
> gparted hides in Settings Manager - has done for at least 2 releases that I'm aware of

@Elfy:

Yes it does, many thanks . . . I thought I checked there, because that is/was where LM stashed it as well, but maybe that was before I rebooted??  Or didn't scroll down far enough??  But, still a bit strange that one of the app launchers wouldn't show it let alone open it??  Anyway, it is now working . . . much appreciated . . . .

@sudodus: I do appreciate the fact that you replied . . . for that I say thanks . . . .

e.e.p.

---

### Post by Elfy on 2014-04-23
> Or didn't scroll down far enough??I rarely scroll in Settings Manager - when I open it - cursor in search box is focussed, so for GParted - I'll type gp and hit enter :)

---

### Post by este.el.paz on 2014-04-23
@Elfy:

That sounds fast . . . I'm all about slow . . . slow motion . . . getting things done slowly . . . that kind of thing . . . .  I'm trying to slowly marked this thread as "solved" but going to the first post is not giving me access to the title, so I can slowly modify it . . . .  When I posted the thread there was the "prefix" box and it had "solved" in it . . . but of course the thread wasn't yet solved . . . but now am not finding it . . . ???  Some of the new list mods are a tad . . . "slow"??? ):P

e.e.p.

---

### Post by Elfy on 2014-04-23
s l o w l y  m a k e  y o u r  w a y  to thread tools - then reallyreallyquicklyhittheMarkThreadasSolved :)

---

### Post by este.el.paz on 2014-04-23
> **Elfy said:**
> s l o w l y  m a k e  y o u r  w a y  to thread tools - then reallyreallyquicklyhittheMarkThreadasSolved :)

@Elfy:

Dang . . . I do click on stuff to try to find the easy answer before posting . . . possibly I was doing it too slow . . . this time I hit it quickly and it seems to have worked . . . .  [Sigh] I don't handle change very well . . . .  =8 ^ 0

e.e.p.

---

### Post by Elfy on 2014-04-23
:)

Have a good day

---

### Post by Xubuntist on 2014-05-01
> **Elfy said:**
> I rarely scroll in Settings Manager - when I open it - cursor in search box is focussed, so for GParted - I'll type gp and hit enter :)

I can only speak for myself, but I have done three Xubuntu 14,04 installs this week (not the same machine!!), two amd64 and one i386, and on each occasion Gparted was not on the install, only on the LiveCD. On the last occasion I checked by typing "gparted" in the Terminal and "gp" in the System properties window. Both came up empty, although in Terminal it actually said it was not there and I should use "sudo apt-get install gparted" to get hold ot it.

Rgds

François

---

### Post by Elfy on 2014-05-02
Gparted is only on the livecd - unless you install it.

---

