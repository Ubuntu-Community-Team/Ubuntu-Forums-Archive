---
title: "Opera 9 install/unistall problem"
date: 2006-06-23
forum: Apple PPC Users
---

### Post by kadymae on 2006-06-23
Have been happily using Opera 9beta, decided to upgrade.

Open Synaptic, check to see that the "multiverse" is checked. Yup.  Type Opera.

Nothing.

Go to Opera  website.  Download Debian Sid package.  Fire up ye olde comand line

sudo dpkg -i otabkeytogettherestofthename

It's installing cthuluspeak

Applications -->Internet -->  I now have 2 Opera icons, neither of which work.

:-k 

okay, I'll just start from scratch.  

Applications --> Add/Remove --> Show unsupported software/Show commercial software checked.  Type Opera into search box ...

Nothing.

:evil: :evil: :evil: 

Now that I'm done honing my sithly rage, how do I convince stupit jedi roadkill Synaptic that no, really Opera is installed and I'd like it to scrub it from the system so I can reinstall and surf the internet in style?

---

### Post by aysiu on 2006-06-23
This may be a good way to find where Opera's hiding: ```
sudo updatedb
locate opera
```

---

### Post by kadymae on 2006-06-23
[QUOTE=aysiu]This may be a good way to find where Opera's hiding: ```
sudo updatedb
locate opera
```[/QUOTE]

Did that and add/remove  **still** can't find Opera, neither can Synaptic.  :(

---

### Post by aysiu on 2006-06-23
The point is that *you* can see where Opera is.

---

### Post by kadymae on 2006-06-23
[QUOTE=aysiu]The point is that *you* can see where Opera is.[/QUOTE]


So, in other words, i need to dig it all out by hand.  :(:evil: 

(poop)

But, thanks for the help, Aysiu.  \m/ you rock.

---

### Post by aysiu on 2006-06-23
I'm not sure how else to approach it. I've always found installed apps (even individual .deb files) in Synaptic. Best of luck.

---

### Post by kadymae on 2006-07-09
> **aysiu said:**
> I'm not sure how else to approach it. I've always found installed apps (even individual .deb files) in Synaptic. Best of luck.

Well, just had a moment to sit down and manually remove Opera.  (If I never have to type sudo rm -r again, it will be too soon.)

Alas, as soon as I reinstalled ... no go.

And it *still* doesn't show up in synaptic, depsite the fact that officially it's supposed to be in the multiverse.  ;P

Guess I'll have to wait until I get a system 76 to see if I can get this going.

---

### Post by RavenOfOdin on 2006-07-10
I tried downloading Opera from the Canonical web repository and GDebi said it was for the i386 architecture.

Any idea when they'll put the PPC version on it?

---

