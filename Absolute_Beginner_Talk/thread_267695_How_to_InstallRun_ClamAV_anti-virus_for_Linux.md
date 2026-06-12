---
title: "How to Install/Run ClamAV anti-virus for Linux"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by newbie8 on 2006-09-29
Hello. I downloaded the ClamAV anti-virus for Linux but can't seem to install or run it.

what am I supposed to do? Extract it? 

But nothing happens after the extraction?

Did I do the right thing?

---

### Post by Mimsy on 2006-09-29
Where did you download it from? Synaptic?

My Clam AV was installed when I installed Ubuntu, and the only things I have downloaded are updates through the update manager.

/Mimsy

---

### Post by newbie8 on 2006-09-29
Yes from Synaptic. I have checked and "apply-ed" so many things from synaptic but can't seem to find them afterwards. I thought an icon clamAv should appear?

Nothing seems to happen after I apply and install?

What are the basic steps to apply and install and run these things from synaptic?

---

### Post by sbergman27 on 2006-09-29
> **newbie8 said:**
> Yes from Synaptic. I have checked and "apply-ed" so many things from synaptic but can't seem to find them afterwards. I thought an icon clamAv should appear?


Clamav is command line only.  Could you tell us what, exactly, you are you wanting clam to do?

---

### Post by newbie8 on 2006-09-29
I used to use clamwin for windows and there was an icon at the bottom which I can just click and then "scan" the computer.

I simply want to see the icon and or scan the computer.

I think I also installed Avast or AVG in the past and I can't seem to find them either.

---

### Post by sbergman27 on 2006-09-29
> **newbie8 said:**
> I simply want to see the icon and or scan the computer.

Well, roll up your sleeves a little. :) 

Go to a terminal (applications->accessories->terminal)

and type:

```
clamscan -r
```

This will scan your home directory and everything under it.  The "-r" means recursive.  You can view the manual page with:

```
man clamscan
```

For all intents and purposes, viruses only exist for Windows.  But clamscan will flag any Windows virus infected files that you may have downloaded or otherwise received.

Unless you are wanting to scan your email messages, or are running a mail server, clamav is probably not all that useful under anything but Windows.

---

### Post by newbie8 on 2006-09-29
Thank you very much sir. Will try it out.

---

### Post by newbie8 on 2006-09-29
Hey it works.

Wish there was a way to know these "command lines".

Where can I find or how would I know which commands to use?

Can I find them anywhere?

---

### Post by sbergman27 on 2006-09-29
> **newbie8 said:**
> Hey it works.
Wish there was a way to know these "command lines".
Where can I find or how would I know which commands to use?
Can I find them anywhere?

Well it's really a whole world unto itself.  Extremely powerful, though.

I just googled a bit for a tutorial and found this one that looks reasonable:

[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

For pretty much any command, you can type:

man command_name

to get the manual page.

e.g. 'man ls' will get you the manual page for the command to list files in a directory.

Of course you've got to know the name first.

This index might be helpful:

[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

You don't have to learn it all at once, of course!  A small subset can be quite useful.

---

### Post by newbie8 on 2006-09-29
Thank you. What you gave is an excellent resource for Ubuntu or Linux-confused newbies like myself.

---

### Post by petri on 2006-09-29
There is a frontend to clamav and it looks like this [http://wolfpack.twu.net/Endeavour2/contrib/#avscan](http://wolfpack.twu.net/Endeavour2/contrib/#avscan)
and you can find it in Synaptic.

---

