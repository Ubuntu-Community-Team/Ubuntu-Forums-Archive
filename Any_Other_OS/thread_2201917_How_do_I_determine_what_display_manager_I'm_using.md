---
title: "How do I determine what display manager I'm using?"
date: 2014-01-26
forum: Any Other OS
---

### Post by PopsTheSailor on 2014-01-26
I have Mint 16 installed and want to change my  login theme. From what I've read, Mint 16 is supposed to have MDM (Mint Desktop Manager)  running. If I go to a terminal and run mdmsetup it says that MDM is not  installed but doesn't tell me what display manager is.

I, hopefully, have attached a picture of the error message. I get the same message whether I use sudo or not.

Is there a command that will tell me what display manager I'm using?

---

### Post by Bashing-om on 2014-01-27
PopsTheSailor; Hi ! once more.

Try:
```

echo $DESKTOP_SESSION

```
Works for 'buntu, highly likely for Mint also.

[INDENT][INDENT]keep'n on keep'n on
[/INDENT][/INDENT]

---

### Post by rewyllys on 2014-01-28
> **Bashing-om said:**
> PopsTheSailor; Hi ! once more.

Try:
```

echo $DESKTOP_SESSION

```
Works for 'buntu, highly likely for Mint also.[INDENT][INDENT]keep'n on keep'n on
[/INDENT]
[/INDENT]

Indeed it does work for Linux Mint, at least for my copy of LM 13. 
 
As evidence:
```
ron@ron-desktop-linux:~$ echo $DESKTOP_SESSION
cinnamon2d
ron@ron-desktop-linux:~$ 

```

---

### Post by Bashing-om on 2014-01-28
hey ;

Under the hood, it's all linux !

[INDENT][INDENT]all in this together[/INDENT][/INDENT]

---

### Post by steeldriver on 2014-01-28
That's the session - not the DM though

I'm not sure how universal this is, but you could use ps to look at where the X server is saving the root Xauthority cookie

```

$ ps -ef | grep '/[X]'
root      1008   990  4 19:28 tty8     00:00:35 /usr/bin/X :0 -audit 0 -auth **/var/lib/mdm/:0.Xauth** -nolisten tcp vt

```

versus

```

$ ps -ef | grep '/[X]'
root      1241  1214  2 Jan23 tty7     03:19:54 /usr/bin/X :0 -auth **/var/run/lightdm/root/:0** -nolisten tcp vt7 -novtswitch -background none

```

or (slightly more elegantly) if you have pstree installed

```

$ pstree -s $(pidof X) # mint13 with mdm
init&#9472;&#9472;&#9472;mdm&#9472;&#9472;&#9472;mdm&#9472;&#9472;&#9472;Xorg

```

```

$ pstree -s $(pidof X) # Ubuntu with lightdm
init&#9472;&#9472;&#9472;lightdm&#9472;&#9472;&#9472;Xorg

```

---

### Post by PopsTheSailor on 2014-01-28
Thanks everyone. I attacked it from a different angle and figured it out. I wanted to use what comes with the standard install so I took my install CD and booted up Mint. I then went into Synaptic and looked to see what DM was installed (print screen and save to my Data partition). I then booted up my installed Mint and went back to Synaptic to see what I had configured. It so happens that I had GDM, lightDM and MDM all installed. They must have been conflicting with each other. I removed GDM and LightDM and left MDM. After that, I rebooted and I was back to base. I had been working on trying to fix my laptop speakers (my last major problem before I'm happy) and was following a thread that had me running all sorts of commands. Those must have installed GDM and LightDM. That's the trouble with being a rookie. When trying to fix stuff, I blindly run commands not knowing their full impact.

I'm going to mark this thread solved.

---

### Post by Bashing-om on 2014-01-28
PopsTheSailor; Outstanding.

More than one way to skin a cat.
To mark as solved (only you can do so): 1st post -> thread tools

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

