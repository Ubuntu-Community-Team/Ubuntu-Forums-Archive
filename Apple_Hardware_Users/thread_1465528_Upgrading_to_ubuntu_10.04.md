---
title: "Upgrading to ubuntu 10.04"
date: 2010-04-29
forum: Apple Hardware Users
---

### Post by Jforce93 on 2010-04-29
Hi everybody,

I tried to upgrade to ubuntu 10.04 today (on my ibook g4) and I got this error:" W:Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/lucid/Release](http://ports.ubuntu.com/ubuntu-ports/dists/lucid/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?) , E:Some index files failed to download, they have been ignored, or old ones used instead." :(  How can I fix this? FYI its the PowerPC version of ubutu

---

### Post by zeroti on 2010-04-29
what I did was edit the /etc/apt/sources.list file.

I had to comment out the line that had the word "partner" in it. However, during the update, the sources list would get replaced for lucid compatability and would lose the comment. So the trick is to replace all of the words "karmic" with "lucid" and then to comment out the necessary line. If you decide to cancel your update, you need to revert the file to get karmic updates.

However, I had a major problem during the upgrade ("update-manager -d"). My mouse and keyboard became unresponsive so I had to hold down the power button when the clean-up phase popped-up a dialogue I couldn't answer. One of my friends said that he just does "sudo apt-get dist-upgrade" or something. If the keyboard would be an issue, I would suggest using the "-y" option. (Also try turning off sleep mode for the computer and screen.) But the drawback of this is that I don't know if the package manager will try to replace itself during the update and thus botch things up that way... so does anyone else know how to do this right without an install cd?

EDIT: Don't forget to uncomment the "partner" line after you update your installation if you still want software from that source.

---

### Post by Jforce93 on 2010-04-29
> **zeroti said:**
> what I did was edit the /etc/apt/sources.list file.

I had to comment out the line that had the word "partner" in it. However, during the update, the sources list would get replaced for lucid compatability and would lose the comment. So the trick is to replace all of the words "karmic" with "lucid" and then to comment out the necessary line. If you decide to cancel your update, you need to revert the file to get karmic updates.

However, I had a major problem during the upgrade ("update-manager -d"). My mouse and keyboard became unresponsive so I had to hold down the power button when the clean-up phase popped-up a dialogue I couldn't answer. One of my friends said that he just does "sudo apt-get dist-upgrade" or something. If the keyboard would be an issue, I would suggest using the "-y" option. (Also try turning off sleep mode for the computer and screen.) But the drawback of this is that I don't know if the package manager will try to replace itself during the update and thus botch things up that way... so does anyone else know how to do this right without an install cd?

Changing the /etc/apt/sources.list file worked. I am downloading the update now :biggrin: and i'm gonna see if it installs. THANK YOU!

---

### Post by B_Free on 2010-04-29
The finished version for PPC is not ready yet.

---

### Post by kensanata on 2010-04-30
> **zeroti said:**
> what I did was edit the /etc/apt/sources.list file.

I can [confirm]("http://www.emacswiki.org/alex/2010-04-30_Ubuntu_10") that this worked. It's entirely possible that B_Free's remark is spot-on. I haven't used much of the system. Firefox works. :)

I wonder where I could get the "official" sources.list from...

---

