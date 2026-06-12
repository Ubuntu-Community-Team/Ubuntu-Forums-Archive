---
title: "Synaptic and Sudo issues running Edgy on a PPC iBook"
date: 2006-12-24
forum: Apple PPC Users
---

### Post by dasmith on 2006-12-24
I am having issues with using Synaptic.  It comes up and tells me that I have 15 updates.  When I click on install updates, it checks for updates and close back to the same box.

When I open the terminal, and run sudo apt-get update I receive the following:

> sudo: unable to lookup MACSucks via gethostbyname()

I also receive another error that relates to issues with sudoer's .  I have several connections I use.  At home and another location I receive these errors.  When I am at a friend of mines, everything works fine.

I have been searching Google and here in the forums and have not been very successful in finding a solution to my issue.  From what I have been reading, I need to go into the recovery console and I am using an iBook G3 running Edgy.  I have been tapping the > ESC key and am not able to find a listing of boot options that list > recovery mode.

any help would be appreciated.  Thank You

---

### Post by elcasey on 2006-12-24
It sounds like some of your core files got messed up, especially the list of repositories. If it says "MACSucks," it sounds like it might've been by malicious software, although you would have had to allow the software to run. 

I don't know if there's a "repair install" option, but that sounds like what you need. If you don't have critical data, just reinstall the OS.

---

### Post by dasmith on 2006-12-24
actually MACSucks is my host name.

I am about ready to do a re-install unless someone can give me any ideas on this.

---

