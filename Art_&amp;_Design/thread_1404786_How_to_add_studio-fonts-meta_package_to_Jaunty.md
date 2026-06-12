---
title: "How to add studio-fonts-meta package to Jaunty"
date: 2010-02-11
forum: Art &amp; Design
---

### Post by bobbiescap on 2010-02-11
Hi,
I generally use my desktop machine for art as it has plenty of grunt, but also own an MSI Wind which I sometimes have to use for design work and picture editing and it performs adequately after I updated it to 2Gb of memory.

The hassle is that Karmic has multiple issues with these netbooks and they are far happier on Jaunty, except that Karmic offers the Ubuntustudio fonts meta package, which is a dummy package that pulls in a bunch of fonts and utilities as dependencies. 

Jaunty does not have this one and I am not sure how to add the repository so that I can pull the Karmic package down as it would take more work than I have time for to load each package individually. I tried downloading the .deb and installing via the gdebi package installer but it didn't download the dependencies and I was left with an error message.

It would be fantastic if somebody can lead me in the right direction here as I need the exact fonts to modify work started on the desktop machine.

---

### Post by sigurnjak on 2010-02-12
You can try something like this :
sudo apt-get --no-install-recommends install ubuntustudio-font-meta

See what happens  , and maybe someone will have better idea  if that does not work .

---

### Post by bobbiescap on 2010-02-27
Serious apologies as I have not been back to this for a couple of weeks, my daughter has been bullied at school and tried some self harm and other stuff so I have been pretty tied up with helping her.

Thanks for the suggestion sigurnjak.

When I tried that command I got this error:

> E: Couldn't find package ubuntustudio-font-meta


I will look further and make sure that the package name is correct but any further ideas are welcome as I need to get this sorted out easily as stress levels from my daughter's situation are through the roof.

---

### Post by bobbiescap on 2010-02-27
Decided to put my troubles to one side and the answer was staring me in the face, so for anybody with a similar problem all I did was add a duplicate line in the sources.list file and change the version like below:

> deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty main universe restricted multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main universe restricted multiverse

Loaded the package and then removed the extra line. Feel like a dummy, it was pretty obvious and makes me less concerned about running different distributions on machines because of compatibility issues.

I know that this is not considered a sensible practice but I couldn't see that it would hurt for adding some fonts?

---

