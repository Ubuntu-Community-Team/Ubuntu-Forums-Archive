---
title: "how I installed Limewire"
date: 2005-03-02
forum: Apple PPC Users
---

### Post by trash on 2005-03-02
I couldn't find a Limewire package that I could install via apt or synaptic, so after installing java from the javappc wiki I downloaded Limewire from their site. Their 'Linux' installer only gave me a .rpm which you will read further on didn't work with Alien.
I downloaded the 'Other' which gave me a .zip file... the rest is explained below taken from a post on the Limewire forum.... maybe there is a better way but this worked well enough for me:)


Posted by ppcuser on 03-02-2005 04:13 AM:

i don't get it, if i download the linux version i get a .rpm and if i download the 'other' version I get a .zip... either way I DON'T get a .bin file??

so I unpacked the .zip and ran ' java -jar LimeWire.jar' (from the read me file).

it did install but I have no icons, in order to start limewire i must navigate to the folder and double click 'runLime.sh'

I'm using the ibm java and limewire does run VERY well... but whats with the install method and icons?

Ubuntu/hoary PPC.

thanks for any help
Posted by zab on 03-02-2005 04:20 AM:

The install instructions in this thread need updating since we switched to new installers. Thanks for reminding us, it will be done shortly.

The .rpm package provides icons if you are using gnome (will probably work on kde as well). You could probably install the rpm on ubuntu using alien, but its not guaranteed.
Posted by ppcuser on 03-02-2005 07:02 PM:

Alien doesn't work, I get an error 'ppc does not appear in package's list (i386).

Since i do have limewire sort of installed and running, what file can i link to, to run it from a destop icon(link)?
BTW I did install from the .zip but i am still iconless.

thanks
Posted by zab on 03-02-2005 07:24 PM:

If you want to create your own desktop icon, runLime.sh is the script which launches limewire. the icon file should be either in Limewire.ico (there may also be a .gif available).

If you can unpack the contents of the .rpm, there is a .desktop file there which takes care of some of the steps for you.

---

