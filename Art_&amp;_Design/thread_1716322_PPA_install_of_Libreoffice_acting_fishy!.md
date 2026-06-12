---
title: "PPA install of Libreoffice acting fishy!"
date: 2011-03-28
forum: Art &amp; Design
---

### Post by erikdstock on 2011-03-28
Hi all- I recently had a problem described in many places around here-after purging openoffice and adding the libreoffice repos, I had some problems installing.

First, there is no package for Libreoffice when i search in the software center until it unfilters itself down to the technical items. what i mean is that when i type "libre" i get one package-"Vagalume last.fm Client" and one option to show the remaining 199 technical items. maybe this is because it isn't an official supported part of the repositories yet? Then again this part might be unrelated.

The REAL problem was that after selecting the package libreoffice the install would immediately fail saying i had an unmet dependency for a package that would not be installed. if i clicked the dropdown arrow the listing would show libreoffice as the package that would not be installed. I got a similar response trying to do it over synaptic or apt-get. 

So i thought maybe it was something about the archive being down (i read about it waiting for an update?). I tried re-adding the archives. Finally I installed the amd64 package from my debs, but I still felt funny... I never use debs unless i have to and now the software center was showing my packages as installed (I even added the libreoffice-gnome package through the SC), but would they get left behind or mess something up when natty comes out?

So it was freakin me out and I just began uninstalling everything. Funny, too, for a moment the software center listed a libreoffice package like always and then libreoffice3 with the description "sorry, this isn't availalbe for this type of computer (amd64)." 

So this morning i uninstalled libreoffice from the software center, then via apt-get purge and apt-get autoremove and am now reinstalling it via software center. it seems to be working... one other thing i just remembered is that before successfulling installing gnome integration two paragraphs up i removed one set of repos--i don't know if it was the first or second i'd added.

long post, but i've been confused and stressed! thanks for your help in figuring this out :) :) :)

---

### Post by 23dornot23d on 2011-03-28
Glad you got it working .... have to be careful with PPA's .... I have found a few times dependency problems can occur after installing some of them , the thing I do is to untick  them in synaptic after getting my download - if they are not needed for anyhing other than one certain package depending on what it is.

I download Cinepaint .... it uses a experimental repository ..... some use development repositories too ...... mixing and matching repositories is never a real good idea.

But sometimes necessary for one program or the latest release like the MATT WALKERs - GIMP repository - obviously to keep updating that package the repository needs to be re-ticked ..... but leaving the added PPA's open all the time to me is not necessary who knows what people put into them .......

The Deb files I find are quite a good way to add things ..... if they are a one off .....[COLOR=Red]** and not in the software centre **[/COLOR]....... most give a warning too if a version is in your repositories.

Not sure what the official line is on PPA's or DEB's .....
But to get the program that you need and it is not in the Software Centre ..... 
Then sometimes PPA or DEB seems the only way to get the package you need ....... 
( Other than by compiling it all by yourself - this I only do as a very last resort in cases where no other means are possible )  .

But glad to see another happy Linux user again ...... :D

---

### Post by Hagar Delest on 2011-03-28
Remember that the PPA reps are not checked so they might lead to problems indeed. I remember the release of OOo 3.0 through the PPA, plenty of topics here afterward because of bad packaging.

Better install the vanilla version from the official LibO site IMHO. Never had any problems at all. See that one for example, the same applies to LibO: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

