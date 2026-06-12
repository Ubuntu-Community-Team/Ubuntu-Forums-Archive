---
title: "Real, real basic."
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Durandall on 2008-04-07
I've been using Ubuntu Studio 7.10 for about a week.  Yesterday, I've decided I'm going to switch to regular Ubuntu... still 7.10 - might even try out the beta for 8.04.

While I used Studio... here's what I've had trouble with - i have a wide screen monitor, and after i downloaded the drivers for my radeon, from ATi - i couldn't install them because i wasn't a "super user" - I'm the only user.  how do I switch to Super?

for now... if i can get the resolution tolerable - i'll stick with it and try to figure most everything else out.  Pretty much... I think I'll have to buy a beginners guide... if i can't handle something as simple as installing something... without joining a forum.  Any recommendations?  I'd like some non-technical descriptions, and instructions that would help me understand like... the partitions... and how to use the um... um... the linux version of command prompt.

if i could understand that... i think Linux and I will do just fine.

Like I said though... for now though... after I install Ubuntu 7.10 - how can i get my radeon drivers installed?

---

### Post by philinux on 2008-04-07
you put 

sudo 

or

gksudo for any app that has a gui in front of the command.

I'd try this for your drivers though.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Michael.Godawski on 2008-04-07
This is also a good site if you are looking for information about installing stuff:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

For your graphic card you can either try the envy application posted above or the restricted driver manager (System > Administration > Restricted Drivers Manager)

---

### Post by Durandall on 2008-04-08
I tried using the restricted drivers manager, and this error come up when i tried to enable it:

The software source for the package

   xorg-driver-fglrx

 is not enabled.

So... how do I enable that?

---

### Post by Boyohazard on 2008-04-08
> **Durandall said:**
> I tried using the restricted drivers manager, and this error come up when i tried to enable it:

The software source for the package

   xorg-driver-fglrx

 is not enabled.

So... how do I enable that?

Try the following line in terminal:

```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by conscious on 2008-04-08
To have it installed, you must enable "restricted" repository in System -> Administration -> Software Sources.

---

### Post by Durandall on 2008-04-08
> **Boyohazard said:**
> Try the following line in terminal:

```
sudo apt-get install xorg-driver-fglrx
```

I entered that into the terminal, and i get this error:


Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages
randall@Ubuntu:~$ 


So, if the package is broken, how do i replace it with one that isn't?

Am i understanding this right??? is a package similar to the .exe from windows?

---

### Post by Durandall on 2008-04-08
> **conscious said:**
> To have it installed, you must enable "restricted" repository in System -> Administration -> Software Sources.

I've enabled the restricted, thing... and i went the extra step to enable third party, and all that stuff... just now - i mean.  thanks for the tip!

then... i got an update advisory... 205 updates!! installed them all, restarted... and i'm still kinda at square one.  just, an updated square one.

and now... something really weird started happening.

---

### Post by stchman on 2008-04-08
> **Durandall said:**
> I've been using Ubuntu Studio 7.10 for about a week.  Yesterday, I've decided I'm going to switch to regular Ubuntu... still 7.10 - might even try out the beta for 8.04.

While I used Studio... here's what I've had trouble with - i have a wide screen monitor, and after i downloaded the drivers for my radeon, from ATi - i couldn't install them because i wasn't a "super user" - I'm the only user.  how do I switch to Super?

for now... if i can get the resolution tolerable - i'll stick with it and try to figure most everything else out.  Pretty much... I think I'll have to buy a beginners guide... if i can't handle something as simple as installing something... without joining a forum.  Any recommendations?  I'd like some non-technical descriptions, and instructions that would help me understand like... the partitions... and how to use the um... um... the linux version of command prompt.

if i could understand that... i think Linux and I will do just fine.

Like I said though... for now though... after I install Ubuntu 7.10 - how can i get my radeon drivers installed?

Use Envy to install the proprietary ATI driver on your system.  Use Envy 0.9.10 and first have it remove any driver that you installed on your system and then have it install the driver.  Let Envy modify your xorg.conf and reboot the machine.

If for any reason you boot into a CLI mode then you can use Envy's CLI via:

```
sudo envy -t
```

If that does not fix the res problem then add "1680x1050" (sub your monitor's desired native res for that value not forgetting the quotes) as the first resolution in the line of resolutions in your xorg.conf.  Reboot the workspace CTRL-ALT-BKSP and all should be fine.

---

### Post by Durandall on 2008-04-08
i don't know what the hell i just did... but now - my max resolution is 800x600.

whenever i restart... i get a message saying my monitor and graphics card have to be configured... so i click the configure button... and then i choose my graphics card ( i have an ATI radeon X1950 - which... is basically a X1900)  then i select my monitor - and it doesn't change anything.  I'm still stuck in 800x600.

can i restore default setting or anything?  earlier today i had a resolution of 1280x1064.  better than what i have now, at least.

---

### Post by Durandall on 2008-04-08
OMG... things just got worse.

So... i figured out how to install envy, finally... and got my ATI drivers installed.  The problem was, I still had my CD-Rom as my source... and now that's working the way it should.

so, i went to settings, administrator, and then screen and size?  is that what it was?  I don't remember for sure... but it's where you tell ubuntu what you monitor is, and what your graphics card is.

i had it set as my sony monitor... and when i changed it to "Generic 1280x1024" - i thought that would solve all my problems.  i did the restart it suggested - and now... i can't see anything!  there is picture... but it's compressed as hell, and not even linear.  how can i revert that?  any possible way, or am i gonna have to completely re-install the OS?

---

### Post by Hendrixski on 2008-04-08
Yikes, sounds like you're in a bind.  I understand what you're going through, I've had lots of problems with stuff and usually I just waited until the next release and it magically got fixed.  Since the next release is half a month away, and it is going to be a Long Term Support release I suspect it's going to have things pretty polished.

I don't know the answer to your problem, but I do just want to say "Hang in there" it's totally worth it.  One resolution problem shouldn't make you think less of the rest of the distro, because there is a LOT of work that goes into making it better and better every day.  I'm glad I stuck around because it has made my work life SSSOOO much simpler.  Hope that helps you stay encouraged :-)

---

### Post by Durandall on 2008-04-08
> **Hendrixski said:**
> Yikes, sounds like you're in a bind.  I understand what you're going through, I've had lots of problems with stuff and usually I just waited until the next release and it magically got fixed.  Since the next release is half a month away, and it is going to be a Long Term Support release I suspect it's going to have things pretty polished.

I don't know the answer to your problem, but I do just want to say "Hang in there" it's totally worth it.  One resolution problem shouldn't make you think less of the rest of the distro, because there is a LOT of work that goes into making it better and better every day.  I'm glad I stuck around because it has made my work life SSSOOO much simpler.  Hope that helps you stay encouraged :-)

Those are some nice words of encouragement, there.  Thank you!

I'm not going to give up on Linux.  I tried probably 6 distros... and Ubuntu is so far my favorite.  It seems like it could be easy, once i get used to it... but there's no telling what kinda time frame that will be.

I'm by no means stranded.  I recently bought a new PC, and turned my old tower into a Ubuntu Desktop.  Once I'm used to it... and i can get all the necessary software - I'll install it on my newer PC and ditch MS all together.

Here's a separate... but related question...  You know all those commands that get typed, or pasted into the terminal?  is there like a web resource for that?  I mean... a database off commands?

---

### Post by Durandall on 2008-04-08
Thank you everyone for your responses.

I just did a fresh, clean install of Ubuntu 8.04 Beta - all of my problems are solved!!

Really... my resolution is set right... i can play back audio and video... (couldn't install the plug-ins earlier, said it conflicted with something in the synaptic program manager)

But... it's all good now!

This raises one question:

Once the official release is out - and I want to install that - how simple is it to not loose all my files and preferences from my current config?

---

### Post by byrmark on 2008-04-08
you can look at my thread.

ati radeon 2400pro + dell wfp, can't get 1680x1050 resolution

STCHMAN's page was quite helpful to me and I used envy to get my resolution to 1680x1050.   It took a couple of tries, but if finally worked after updates, etc.

---

