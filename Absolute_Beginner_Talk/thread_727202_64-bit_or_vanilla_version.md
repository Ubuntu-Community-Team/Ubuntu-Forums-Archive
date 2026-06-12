---
title: "64-bit or vanilla version?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by javafiend on 2008-03-17
Well, now that I hear EQ2 is finally playable on Linux distros, I'm tempted to give Ubuntu another shot.  I have an AMD 64 bit processor and was wondering if I need to go with the 64-bit version or just go with the standard Ubuntu release.  Also, would one play EQ2 better than the other?

Thanks!

---

### Post by mcdan on 2008-03-17
the standard version would work fine... and has better support for most hardware.  i'd go with the 32 bit, unless you have a significant reason to use 64 bit

---

### Post by sayakb on 2008-03-17
There are no hardware compatibility issues with 64-bit editions. All amd64 drivers are available, plus, all 32-bit packages can be easily installed under 64-bit with just a "force architecture" option added to the package manager..

---

### Post by javafiend on 2008-03-17
> **LinuxIsInnovation said:**
> There are no hardware compatibility issues with 64-bit editions. All amd64 drivers are available, plus, all 32-bit packages can be easily installed under 64-bit with just a "force architecture" option added to the package manager..

"Force architecture" sounds intimidating.  I'm all for a challenge, but like most people, when I want to do something, I want to do it NOW.  Will something like "force architecture" prevent me from running any 32-bit apps/packages or whatnot?

---

### Post by sayakb on 2008-03-17
force architecture will not "prevent" anything.. it would just allow direct installation of x86 packages (those which are NOT architecture independent) in an amd64 OS.. I myself installed Avast antivirus, the drivers for my fingerprint reader, and a  DOS Emulator, which were all x86 packages, but work just fine with 64-bit.. I'm using amd64 for quite a while without a single problem.. The only problem which was earlier there with feisty (unavailability of flash plugin) has been solved under gutsy as the flash plugin is included under the repos..

---

### Post by CJ56 on 2008-03-17
I've got an AMD 64 x2 processor in the box & have tried 64-bit & 32-bit versions of Ubuntu.

Bearing in mind that I almost never do anything really processor-hungry on my machine, I found that the 64-bit was, yes, a bit quicker. But with the 32-bit at the moment, you never run into snags getting things to work - so I took the easy option and stuck with 32-bit. And it's still pretty quick...

---

### Post by sayakb on 2008-03-17
> **CJ56 said:**
> I've got an AMD 64 x2 processor in the box & have tried 64-bit & 32-bit versions of Ubuntu.

Bearing in mind that I almost never do anything really processor-hungry on my machine, I found that the 64-bit was, yes, a bit quicker. But with the 32-bit at the moment, you never run into snags getting things to work - so I took the easy option and stuck with 32-bit. And it's still pretty quick...

What exactly didn't work under the amd64 edition that is working with the 32-bit one?

---

### Post by javafiend on 2008-03-17
Well then, sounds like I need to leave work and get started on my 64-bit install.  I'm sure by the time something doesn't work I'll be able to find the answer here.

---

### Post by xc3RnbFO8P on 2008-03-17
Vanilla

---

### Post by sayakb on 2008-03-17
Actually, give 64-bit a try.. Upgrade to the latest packages, and it should work for you.. Of course, there is always an option to come back to the vanilla version of yours, in case the 64-bit one lets you down..

---

### Post by TimelessRogue on 2008-03-17
Why would you use the 32-bit version rather than the 64-bit?  Rumors of hardware incompatibility, with a few exceptions perhaps, are unproven as yet.  Just upgraded from Gutsy to Hardy 32 and then on to Hardy 64 during the past several days on my HP dv6323ed  (AMD64 duo-core) with no problems encountered as of yet.

So I would say to just go for it and install Hardy 64.  If you have any problems related to 64-bit specifically that can't be or haven't been addressed, then by all means reinstall with Hardy 32.  Or if you feel the least bit uncomfortable with going the 64-bit route, then stick with 32-bit.

You might want to use the 64-bit Live .iso to check things out and see if everything is running okay on your box before installing.  After all, that's what it's there for ...

And whichever route you decide to take, good luck and enjoy ...

---

### Post by bruce89 on 2008-03-17
> **TimelessRogue said:**
> Why would you use the 32-bit version rather than the 64-bit?  Rumors of hardware incompatibility, with a few exceptions perhaps, are unproven as yet.  Just upgraded from Gutsy to Hardy 32 and then on to Hardy 64 during the past several days on my HP dv6323ed  (AMD64 duo-core) with no problems encountered as of yet.

Indeed, the only thing I can think of is obselete stuff like w32codecs or something.

---

### Post by sayakb on 2008-03-17
Correct.. Plus with all the amd64 gstreamer packages and VLC, we never need those w32codecs..

---

### Post by javafiend on 2008-03-17
It doesn't sound like there is any reason not to go with the 64-bit version.  And it sounds like if I have any trouble I can switch without much trouble.

Well, hopefully my next post won't be from a Windows box :)

---

### Post by javafiend on 2008-03-17
Well, I did it.  My Windows partition is gone and now there is only Zule... err Ubuntu.

---

### Post by Nythain on 2008-03-17
since this is a "should i" thread and im assuming you are looking for the opinions of many to help you with this decision, ill throw in my two cents.

There is absolutely NO reason you shouldnt be running 64bit ubuntu with a 64bit processor...

I recently made the switch after upgrading my computer parts... i was hesitant at first, remember so many horror stories of driver incompatability, flash problems... etc.

Well... let me say... it all went seamless... after reading a little on the 64bit section of the forums, there were a couple good guides and a great script for installing flash and firefox/swiftfox/any mozilla browswer... it was all i needed to have my system up and running in no time...

not that you will notice significant changes/improvements, they are there, and its a waste to not fully use your processors complete potential... go for it :)

---

### Post by javafiend on 2008-03-18
Thanks for all the replies, they were very helpful with deciding to go with the 64-bit version.  I am up and running now and everything seems to be running ok except... EQ2.  I followed the install directions, did the r_font_(blah, forgot the rest) hack, and ran it with Wine.  If anyone has any experience getting EQ2 to run on 64-bit Ubuntu, please feel free to enlighten me :).  In the meantime I will be diligently searching forums and google.

Thanks again!

---

### Post by javafiend on 2008-03-19
I'm surprised nobody pointed me to this thread "[ Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides) ]("http://ubuntuforums.org/showthread.php?t=368607")".  Looks like everything a 64-bit investigator needs to know is contained in it.

---

