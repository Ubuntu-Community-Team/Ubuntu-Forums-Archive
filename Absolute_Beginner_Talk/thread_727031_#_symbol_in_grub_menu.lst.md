---
title: "# symbol in grub menu.lst"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by pjhartt on 2008-03-17
I have a problem with my laptop not turning off when after shutting down Ubuntu 7.10 desktop i386 for 32bit.

Via the search web and forums, it was suggested that adding acpi=force to defoptions it would sort the problem out. It has not.

The original line was 

# defoptions=quiet splash

This is how I added it

# defoptions=quiet splash acpi=force

I am new to Linux. I don't know what the # means some lines have have ### others ## and this only #. Other line do not have any. Is it that lines with no # are executed and all others with # are not.

Only simple answers please not technical ones.

Regards
Peter

---

### Post by taurus on 2008-03-17
You need to remove the # in front of the line.

---

### Post by SanderVermolen on 2008-03-17
There's a very simple answer to that:

Everything behind a # are comments. They are just ignored by the program using the file. This means it wouldn't have made a difference if you would have written:

# defoptions=quiet splash acpi=force

or

# SOMETHING ELSE

Try to remove the # if you want the line to have any effect, like:

defoptions=quiet splash acpi=force

---

### Post by scorp123 on 2008-03-17
> **taurus said:**
> You need to remove the # in front of the line. Not for the "# defoptions" line! **[COLOR="Red"]That was bad advice![/COLOR]**

Taken from "menu.lst" itself:
```

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

[COLOR="Red"]## DO NOT UNCOMMENT THEM, Just edit them to your needs[/COLOR]
``` ... and guess what? The "# defoptions" line is part of that, so you're not supposed to uncomment it!

---

### Post by scorp123 on 2008-03-17
> **SanderVermolen said:**
>  Try to remove the # if you want the line to have any effect, like: defoptions=quiet splash acpi=force **[COLOR="Red"]Wrong![/COLOR]** 

People, this isn't a guessing contest here. Either read the docs please or keep quiet, but please stop giving people bad advice!

Just a suggestion.

---

### Post by scorp123 on 2008-03-17
> **pjhartt said:**
>  The original line was:
# defoptions=quiet splash

This is how I added it:
# defoptions=quiet splash acpi=force  Good. And now for the changes to take effect you have to update the "grub" boot loader. So you open a terminal and issue this command:
 **sudo update-grub**

(when it asks for a password: that should be your own password. And the password is never ever echoed back, e.g. no stars, no question marks, no sign that whatever is being typed is being accepted ... Just type it in blindly and hit the enter key).

A few messages should fly-by over the screen about stuff having been written to your boot loader. As long as none of those messages say "Error!"-something, everything is OK.

When you reboot the options should now be active. You can check after the reboot with this command:
**cat /proc/cmdline**

That should spit out all the parameters that were used to boot your kernel and it should therefore also mention the new parameter "acpi=force" which you added above. If I do that here I get this:

```
root=UUID=169b894f-8c23-41b5-a895-a9c7d101c6a8 ro splash vga=791 resume=/dev/sda10 
``` ... So the output you will get will most likely be slightly different but it should mention "acpi=force" towards the end of the output.

So if the line is there but your laptop is still having trouble to properly turn off after a shutdown, we could try a few other things too. The "acpi=force" command may help in some cases, but in some other cases it doesn't.

Could you tell us more about your laptop? Make + model? Year it was built? BIOS versions? CPU type? ... To know these things can help a great deal.

---

### Post by Nythain on 2008-03-17
HOLY CRAP... i cant beileve not only someone, but many ones, said to remove that #
word, keep that #

im not sure if its been mentioned, but its probably not taking effect yet, because you have to add it also, further down in the file, for each kernel entry, like you did in defoptions... all the defoptions does, is sets default options that will be added if/when there's a grub update (like when you install a new kernel)

also the effects wont take place untill you reboot... sorry if that was a double up on the info, but i was to blown away by people instantly spamming "remove the #"
people, if you arent familiar with what the poster is asking, for the love of god, dont respond

---

### Post by forrestcupp on 2008-03-17
Well, in most configuration files, # does mean it's a comment.  Grub is slightly different.

Not having any #'s at all means it's an entry for a kernel or OS to boot to.  Only having one # means it's an overall grub option.  Having more than 1 # means it's a comment.

But in most config files, it only takes 1 # to comment.  So people really shouldn't be bashing the ones who said to remove it.  If you don't already know grub works that way, it's a logical thought.

And it is right that you do need to reboot before it takes effect.  If it still doesn't work, try putting # acpi=force on a different line.

---

### Post by bodhi.zazen on 2008-03-17
Put the acpi=force on the kernel line and reboot.

Like this ;

> title Ubuntu, kernel 2.6.17-10-generic
root (hd1,0)
[/b]kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash acpi=force[/b]
initrd /boot/initrd.img-2.6.17-10-generic
savedefault
boot

If that works, add it in where you did (this will configure future kernel updates).

In gurb:

## Two hash = comment
#    One hash = configuration

Typically, in most config files,
# One hash = comments

One last piece of general advice, when editing config files

1. Make a back up copy first
2. Comment your changes.
3. Read the comments teh authors put into them, they are there to help you.
4. Back up your manually configured file (config files are sometime over written by updates).

---

### Post by pjhartt on 2008-03-17
Thank you for your replies

I have done this as suggested

sudo update-grub

cat /proc/cmdline

and added the acpi=force to the kernal

and the update worked, in that when I did the cat /proc/cmdline it said 

root=UUID=790d6d30-ebca-482a-b08e-132746698f2d ro quiet splash acpi=force

But (big BUT) my laptop still does not shutdown. The backlight is still on and the fan is running. It stops at that point and the only way I can turn it off is to hold the power button down until it turns off. Then same happens when I use Hibernate.

Are ther any other suggestions?

Regards
Peter

---

### Post by bodhi.zazen on 2008-03-17
you are unlikely to get the answer to those questions in a thread titled "# symbol in grub menu.lst".

Start a new thread titled with a description of your problem / question.

"Laptop not turning off"

"Fan runs non-stop"

Or some such.

---

### Post by pjhartt on 2008-03-17
Many thanks I have started a new thread as you suggested.

---

### Post by igknighted on 2008-03-17
> **forrestcupp said:**
> So people really shouldn't be bashing the ones who said to remove it.  If you don't already know grub works that way, it's a logical thought.

I agree with the principle of this... but no one was personally attacked here or "bashed".  There was a reminder to only post instructions that you are familiar with, which (in the situation) was a needed reminder.  I don't think it means that those who posted to remove the # whould have just kept their comments to themselves, but a "I haven't dealt with grub, but in general __________" warning would have been proper form.  Especially in a situation like this that could have left the OP's computer unbootable.

@ the OP, a little reasoning behind why this is a special config file and "breaks the rules":

Most config files are read by the operating system once it is booted up.  They are read in by a program and parsed, and the linux standard uses a # to signify comments.  I suspect (although do not know) that this goes back to the shell interpreter using a # to signify comments.  Either way, it is a convention of the OS alone.

Grub is a stand-alone program, it doesn't even run with the kernel booted.  It uses its own standards for naming drives, reading config files, and pretty much everything else.  It is not a part of linux, as you could (in theory) install it to multi-boot any number of operating systems,  without having any of them be linux.  As such, the linux standards do not apply to grub.  In the future, when grub 2 is the standard (instead of the current version), I believe it will comply more with linux standards and things could change, but for the time being consider anything to do with grub to be its own entity.

---

### Post by scorp123 on 2008-03-18
> **pjhartt said:**
>  But (big BUT) my laptop still does not shutdown. Can you tell us more about your Laptop? What brand? What model? How old? These are important details which can help to isolate the problem.

---

### Post by pjhartt on 2008-03-18
It is a Zoostorm 4-6612 15.4" Advanced Vista Premium Media Laptop

Intel Core 2 Duo 2.0GHz, 1GB RAM, 120GB HDD, 256MB ATI X1600, Wireless LAN, TV

I'm am running a dual boot with Vista and Ubuntu desktop 7.10 i386 looking to eventually dump vista

Although the shut down or Hibernate does not work I Restart does.

---

### Post by scorp123 on 2008-03-18
> **pjhartt said:**
> It is a Zoostorm 4-6612 Never heard about that brand. And Google doesn't really give many results back, so I have to assume this is a rather exotic brand. That's unfortunate, because with better-known laptop brands (Dell, HP, Toshiba, Sony, Fujitsu-Siemens, Apple ...) it's easier to find information.

So I will have to guess here.

So **"acpi=force"** did not help. So let's try a few other parameters, OK? You'd add them in the same place where you added **"acpi=force"** and then try and reboot. Important: once you rebooted type in this command:
```
dmesg
``` ... And post the output here. It will be lots and lots of lines, but I think to really understand how your laptop reacts to these parameters we have to see what your kernel responds to those lines we are feeding it with.

One parameter I'd suggest is this combo:
**pci=bios acpi_sleep=s3_bios**

... Taken from my own post here:
[http://ubuntuforums.org/showpost.php?p=3752649&postcount=267](http://ubuntuforums.org/showpost.php?p=3752649&postcount=267)

This under the assumption that your Zoostorm's BIOS might be somewhat similar to my HP dv2108ea's ... Can you try if this works?

If it doesn't work we will have to try something else.

---

### Post by pjhartt on 2008-03-19
This did not work thre first time and I had to rebuild from a back up. 

I put the pci=bios acpi_sleep=s3_bios in def options and in the kernel. This caused a system failure.

I then put just in defoptions and It rebooted OK but it still does not shut down. I have attached my menu.lst and the dmesg results. 

Don't forget I am just a beginner in Linux

---

### Post by scorp123 on 2008-03-19
> **pjhartt said:**
>  I put the pci=bios acpi_sleep=s3_bios in def options and in the kernel. This caused a system failure. Oh :( ..... OK; try this one: ```
pci=usepirqmask
``` I had to do this for one of my Fujitsu-Siemens laptops, so maybe this will do the trick? I suggest you follow **bodhi.zazen**'s suggestions (a few postings above mine) on how to add those options temporarily so it doesn't render your laptop unbootable.

---

### Post by pjhartt on 2008-03-20
I have tried this with no change in results.

Attached is a zip file of menu.lst and dmesg results.

I has been suggested that I upgrade the BIOS. I have looked and there are two versions. One is for Windows XP, the other for Vista. As I am running a duel system with Vista at the moment, this is the one that I intend to use. I will not do this until until advice from you.

Regards
Peter

---

### Post by scorp123 on 2008-03-21
Sorry ... running out of ideas here. Maybe you could call the manufacturer of that laptop and ask them what the right parameters are so the laptop would properly shutdown under Linux?

---

### Post by pjhartt on 2008-03-21
Thanks anyway

---

### Post by scorp123 on 2008-03-21
Something you could still try .... I was once involved with Linux Mint. Not anymore though. Long story. But in another thread someone mentioned that the current Linux Mint 4.0 release worked better on his laptop than the current Ubuntu releases. Maybe you could try that? Linux Mint is based on Ubuntu, so it's similar enough, but the kernel is configured with different options (= different from what Canonical Inc. think is "right" or not) so maybe this will "just work" on your laptop? Try it. I mean ... you have nothing to lose, right? You can only win.

[http://www.linuxmint.com](http://www.linuxmint.com)

=> look out for "Linux Mint 4.0  -- **_Main Edition_**" ... That's the one you will want. It comes with codecs, multimedia support and Gnome and everything.

---

### Post by pjhartt on 2008-03-21
I see 2 versions so far

Linux Mint 4.0 KDE CE and Linux Mint 4.0 Daryna

Which would you suggest?

Peter

---

### Post by scorp123 on 2008-03-21
> **pjhartt said:**
> I see 2 versions so far: 
Linux Mint 4.0 KDE CE and Linux Mint 4.0 Daryna  Go to the "Downloads" page where all releases are listed. The "CE" releases are "Community Edition" releases, so they're not really from 'Clem' (the creator of Mint) but rather from someone in the forum (hence the name ...). What you'd need is clearly the "**Main Edition**".

---

### Post by pjhartt on 2008-03-21
I have now also found versions going back to 1.0 Ada

---

### Post by pjhartt on 2008-03-21
I have tried the Linux Mint 4.0 Daryna but that does not turn off either.

I will try an earlier verion.

Peter

---

### Post by pjhartt on 2008-03-25
I have tried the earliest version of MintLinux I could get 2.0, this made no difference and have gone back to the MintLinux Daryna 4.0. I have updated my BIOS and this has made no difference. 

Should  I try everything that I previously tried in the Ubuntu Desktop 7.10 again i.e. 

acpi=force
pci=bios acpi_sleep=s3_bios
pci=usepirqmask

Regards
Peter

---

