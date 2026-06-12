---
title: "swf-player problems"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by gsub on 2008-01-16
Hello, everyone.

I already have libgtk2.0-0, and I'm trying to install swf-player (tried synaptic as well as apt-get).

If I use synaptic, I get something on the lines of "To be removed : <Pretty much every application i have on my PC>",

"To be installed: libgtk2.0-0" 

and i didnt want to proceed at that point.

If I try apt-get, I get the following error message.

"
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
swf-player: Depends: libgtk2.0-0 (>= 2.10.3) but it is not going to be installed
E: Broken packages
"

I tried reinstalling libgtk2.0-0, to no avail.

Could someone please help?

Many thanks.

---

### Post by philinux on 2008-01-16
[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)

If I read you right, this will play flash just download it to your desktop and double click it.

---

### Post by gsub on 2008-01-16
i tried installing the flash player available from adobe's website, but it seems to have problems with some websites, say radioblogclub.com

i used to have swf-player, and that worked the best with all websites i visited, but had to format my pc and reinstall gutsy, and now i get error messages.

FYI, there dont seem to be any broken packages, as reported by synaptic.

any ideas?

thanks.

---

### Post by gsub on 2008-01-16
<bump>

---

### Post by c0met on 2008-01-16
I had a similar problem. It turned out to be the order in which programs and libraries were installed. I just made a note of which ones had to be installed and then installed them individually. That worked for me. One other thing that you might try is to install Gnash as it might load in the libraries you need. You can then uninstall it and try installing Flash. (I'm assuming your computer has a 32 bit processor)

---

### Post by gsub on 2008-01-17
Sorry for the late reply, c0met, but could you please elaborate on what you did? (the list thing). Installing and removing gnash didnt work.

---

### Post by c0met on 2008-01-17
What is your version of libgtk? When I check mine in Synaptic Package Manager, it tells me that my installed version is 2.12.0-lubuntu3.

After reading all your posts thoroughly, I see that you  have essentially tried to manually correct things. Are there any other files that also need to be installed along with libgtk?

---

### Post by gsub on 2008-01-17
i have the same version: 2.12.0-1ubuntu3

other packages that need to be installed: there's a whole list under the dependencies for swf-player.

:confused:

---

### Post by c0met on 2008-01-18
I'm sorry, but I don' t have any more ideas.

---

### Post by gsub on 2008-01-19
Seems like I stumbled upon a bug - and I'm not the only one..

[http://ubuntuforums.org/showthread.php?t=654552](http://ubuntuforums.org/showthread.php?t=654552)

---

