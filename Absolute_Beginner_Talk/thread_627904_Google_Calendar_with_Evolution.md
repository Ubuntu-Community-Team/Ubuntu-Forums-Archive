---
title: "Google Calendar with Evolution"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by LRT on 2007-11-30
I've recently loaded my Google calendar into Evolution, but as it is known this is a read-only access. i can see the calendar, but i can't make any changes to it. 

i heard a two way sync will be available when the new stable version of Evolution comes out (2.21).

does anyone know when that will be released???? has anyone been able to use the calendar with two way sync in the 2.21 unstable release??? does it work???

please let us know.

---

### Post by kelbizzle on 2007-12-01
yes 2.21 unstable will work. [http://johnnyjacob.wordpress.com/2006/04/30/google-calendar-in-evolution/](http://johnnyjacob.wordpress.com/2006/04/30/google-calendar-in-evolution/)

---

### Post by LRT on 2007-12-02
thanks for your reply.

i recently finished installing 2.21 but now i get this error when trying to start evolution.

"Evolution can not start. Your system configuration does not match your Evolution configuration."

i read this solution ([http://www.go-evolution.org/FAQ#What_does_.22Your_system_configuration_does_not_match_your_Evolution_configuration.22_mean.3F]("http://www.go-evolution.org/FAQ#What_does_.22Your_system_configuration_does_not_match_your_Evolution_configuration.22_mean.3F"))and tried it but still no joy. i think it is some simple configuration i am not aware of. any idea????

---

### Post by HellBoyz77 on 2007-12-10
Same problem here, tried the Evolution FAQ with no success.

---

### Post by hugmenot on 2007-12-10
I built the Evolution 2.21.3 from hardy for Gutsy in my PPA. That is, I made a backport. It works so far. If you want, you can test it, but there's more unstable stuff in my PPA, so you would have to add the APT source, install specifically Evolution, and then remove the source to not get the other stuff on the next upgrade.

EDIT: removing the links to my PPA, because some breakage occured for users below, who installed more than Evolution.

---

### Post by philinux on 2007-12-10
If you want something that works now until evolution is sorted, try thunderbird with the lighting calendar extension. Works a treat.

---

### Post by LRT on 2007-12-10
even that has its own problems. lightning 0.7 won't with thunderbird 2.0 on gutsy. all you get is a bunch of colored bars where the calendar is supposed to be.

---

### Post by philinux on 2007-12-10
You might have a graphics card problem I think.

---

### Post by Kimos on 2007-12-11
hugmenot:
Thanks for the repo! Made updating to newer than 2.12.0-0ubuntu5 quick and painless.

---

### Post by facted on 2008-01-05
Thanks for the work! Unfortunately, on my system, installing the latest evolution from your deb breaks evolution entirely and it won't even start (and no message appears). Perhaps it's 2.21.4? Is that version working on your system?

---

### Post by AldenIsZen on 2008-01-05
Being that I read your post 18 minutes after you posted it, I thought I would respond ASAP. I am a inexperienced Linux user, but what I did was try to open Evolution in a terminal. That gave me an error about missing file libpixman.. I could install it via Synaptic, but instead I reactivated or re-added the first line that hugmenot gave. I then disabled all updates EXCEPT the libpixman file.. and Evolution started. (Don't forget to disable the repo again..) I haven't had time to test the sync with Gmail  just yet.. like I said just trying to get this to you.

---

### Post by facted on 2008-01-06
Thanks very much for the help! Worked like a charm.

---

### Post by AldenIsZen on 2008-01-06
No problem. However, Evolution seems to be crashing, and I haven't quite figured out the "rules" for synchronization. It seems that if I create something in Evolution and delete it in Gmail that it still stays in Evolution..  I need to take the time to sort it out I guess.

---

### Post by Maupertus on 2008-01-23
Hi guys, 

I added the repository but did a sudo apt-get upgrade. After which my system borked.
Everything works, but I lost all my graphical settings, evolution isn't updated and everything is really slow.

Does anybody know what happened and if I can reverse it?

Edit: Okay, I've lost NTFS support. I can't access my filesystems....I know there were some unstable packages but...

---

### Post by hugmenot on 2008-01-23
Really sorry to hear this. If you would tell me more about how the upgrade came out (conflicting packages, etc) then I might help to navigate you out of this. I know that libbeagle leads to conflicts, because nautilus depends on another version. The consequence is that Nautilus won't start.

If you run "aptitide dist-upgrade" what is the output before you enter "yes"? What is the state of your system, i.e., what doesn't work? I cannot imagine how your NTFS could be affected by my repo. There's nothing in it pertaining to NTFS.

*goes to remove the above instructions*

---

### Post by Maupertus on 2008-01-24
Nah, you don't have to remove them, I just added your repo in Synaptic because I was working in it anyway. Then I didn't think and instead of adding the lines you posted in terminal, I mechanicly updated and upgraded as I always do when in Synaptic (or when in terminal, it's usually my last to commands)

I was just a little bit scared freaky yesterday.

But Nautilus is one problem, are there any Compiz rep's in there, because my desktop is slow and borked as well. Same with my Desktop finding WiFi.

I'm not at home right now, but I will post when I can.

On a good note, I have now got a bleeding edge Evo ;)

---

### Post by Maupertus on 2008-01-24
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      


this is my ouput with aptitude dist-upgradI

I solved the nautilus problem as it was posted here: [http://ubuntuforums.org/showthread.php?t=652477&highlight=libbeagle0](http://ubuntuforums.org/showthread.php?t=652477&highlight=libbeagle0) 

I have attached a picture of my desktop. Indeed, I can acces my NTFS disks, but they don't show up mounted on my desktop. It's as if I don't have a desktop anymore.
Booting is also extremely slow.

As stated, wifi is a bit dodgy as well.

Thanks for helping me fix my own mistakes ;)

Any other tips how to get back to before (or better?)

Thanks!

---

### Post by hugmenot on 2008-01-25
Well, and sorry for the delay, that you don't have icons on your desktop is because Nautilus doesn't start up. It draws the desktop surface and the icons, after all.

Your dist-upgrade tells us, that there are no package conflicts, which is good, I guess. Does Nautilus start up, now that you downgraded to the official version of libbeagle? Do you have icons on your desktop?
You can look for the display filter in Synaptic that displays installed packages by source (I know it exists, look for it). Then, in the ppa/launchpad item go to the (lib-)beagle packages and downgrade them to "gutsy/ubuntu.com" (or something like this).
Then, I have newer versions of "dbus" and "hal", because my unstable install of network-manager requires them. They don't exactly pertain to wifi, or compiz, but it might help to donwgrade these, too.
You can look at [this listing]("https://launchpad.net/~towolf/+archive") to see what you unknowingly might have upgraded to.

---

### Post by AldenIsZen on 2008-04-25
Di you still have 2way syncing working hugmenot?

---

### Post by hugmenot on 2008-04-26
Actually with the standard Evolution in Hardy writing events doesn't seem to work. (check launchpad for bugs.)
But anyway,  the worst part has always been that, back when it still worked, Evo wouldn't enable my default SMS reminder. Which is the whole advantage of using Gcal for me.

So now I have something better. I use gcalcli (from universe) and a bash alias to "quick add" events to my Google Cal now.

```
function qa() {
gcalcli --user hugmenot --pw ***** quick "$*"
}
```

And you can run this from the run box for example with natural language input: 
"qa table tennis with elif tomorrow 20:00"

---

### Post by AldenIsZen on 2008-04-27
Interesting.. sounds like an opportunity to learn! :popcorn:

---

### Post by Ghuloomo on 2008-05-01
> **hugmenot said:**
> Actually with the standard Evolution in Hardy writing events doesn't seem to work. (check launchpad for bugs.)
But anyway,  the worst part has always been that, back when it still worked, Evo wouldn't enable my default SMS reminder. Which is the whole advantage of using Gcal for me.

So now I have something better. I use gcalcli (from universe) and a bash alias to "quick add" events to my Google Cal now.

```
function qa() {
gcalcli --user hugmenot --pw ***** quick "$*"
}
```And you can run this from the run box for example with natural language input: 
"qa table tennis with elif tomorrow 20:00"

Could you please tell me how it works?
The gcalcli I can install it no problem, but what is this?
```
function qa() {
gcalcli --user hugmenot --pw ***** quick "$*"
}
```

---

### Post by hugmenot on 2008-05-01
Just a shortcut you can enter in .bashrc in your home directory. 

So I only have to enter "qa blah blah" instead of the full command.

---

