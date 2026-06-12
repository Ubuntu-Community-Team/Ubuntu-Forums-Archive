---
title: "Error in &quot;create a bootable USB stick on OS X&quot;"
date: 2012-05-27
forum: Apple Hardware Users
---

### Post by Lars Noodén on 2012-05-27
The web page "[Create a bootable USB stick on OS X](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx)" has an error in step 3.  The syntax for using hdiutil is wrong.  The way it is used in the example creates an error:
```

$ hdiutil convert -format UDRW -o /tmp/target.img ~/Downloads/lubuntu-12.04-desktop-powerpc.iso

Usage:	hdiutil convert -format <format> -o <outfile> [options] <image>
	hdiutil convert -help   

```

I'm unable to guess the correct way of using hdiutil to convert the disc image.  What is the correct way to use hdiutil there?

---

### Post by gwjvan on 2012-05-27
Are you interested in making the live usb, or interested in updating the instructions?

If you just want a bootable usb stick from an iso, have you tried dd? Here's an example of a dd command for a powerpc usb image I created (run in a mac terminal):[INDENT]dd if=precise-alternate-powerpc.iso of=/dev/disk1 bs=1m
[/INDENT]If you do it from linux, I think the final "m" has to be capitalized, for example:[INDENT]sudo dd if=precise-alternate-powerpc.iso of=/dev/sdb bs=1M


[/INDENT]Edit: Whoops, I didn't read that instructions page to the end. The point was to make something that all you have to do is hold the option key down at startup? (And they use dd on that page anyway... my bad)

---

### Post by gwjvan on 2012-05-27
Looks like you have to move the .iso filename to right after "convert"

this worked for me:[INDENT] hdiutil convert ~/Documents/quantal-desktop-powerpc.iso -format UDRW -o ~/Documents/quantal.dmg
[/INDENT]Edit: Okay, quantal.dmg mysteriously disappears when it finishes for some reason...

When running hdiutil in verbose mode, it returns:[INDENT]hdiutil: convert: result: 22[/INDENT]Can't find what that means- another poster thought it meant the iso was faulty.

If others can't get hdiutil to work, they may just have to dd the .iso and hold command+option+o+f on startup

---

### Post by nm_geo on 2012-05-28
> **Lars Noodén said:**
> The web page "[Create a bootable USB stick on OS X]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx")" has an error in step 3.  The syntax for using hdiutil is wrong.  The way it is used in the example creates an error:
```

$ hdiutil convert -format UDRW -o /tmp/target.img ~/Downloads/lubuntu-12.04-desktop-powerpc.iso

Usage:    hdiutil convert -format <format> -o <outfile> [options] <image>
    hdiutil convert -help   

```I'm unable to guess the correct way of using hdiutil to convert the disc image.  What is the correct way to use hdiutil there?

Hey Lars.. Did you create the simple dd - USB in linux and get it to boot?  I just wiped this PowerBook G4 it only speaks Linux now, but it will be ready for the qq 12.10 Alpha spins. Yes, I have got the wireless worked out as well.

Now, I need to try a persistent USB for the powerpc iso.  It is not as easy as the i386 or amd64 isos.  

Maybe I will try out a couple of the pre- Alpha spins before Alpha 1 arrives, just to make sure I can get them to install. 

  Be Well.
nm_geo Greg

---

### Post by Lars Noodén on 2012-05-28
> **nm_geo said:**
> Hey Lars.. Did you create the simple dd - USB in linux and get it to boot? 

I used dd on Linux to copy the ISO image to the USB stick.  It shows up if I hold down Alt when booting, but does not go further.  Selecting it from the menu does not do anything except return to the Alt menu showing the systems already installed.  So, no, I did not get it to boot.

---

### Post by Lars Noodén on 2012-05-28
> **gwjvan said:**
> Looks like you have to move the .iso filename to right after "convert"

That's what I thought, too.  But hdiutil still does not do the conversion and only prints up usage info.

---

