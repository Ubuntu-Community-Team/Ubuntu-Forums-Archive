---
title: "Need to fully set-up my system."
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-10-25
Hey folks. Okay, so I've gotten mega lazy due to work and home issues for the last while, and I haven't actually been very ubuntu-intensive. My lap-top is currently running on Feisty and I want to upgrade to Gutsy. I'm not able to do this, because of a 404 error in apt-get. I haven't been able to figure out what's happening, although I think it's one of my repo lists that's wonky. I removed one that was for Edgy, and now, because of that I think Gmail isn't showing up although the page claims to be successfully loaded. 
I really want my system to be fully operational, and I'm really not a guru in any sense when it comes to this sort of thing. That only means that I just don't know how to ask the right questions, only tell people what's happening.
So again, Gmail isn't appearing, nor is my Google homepage. I can't upgrade or run apt-get because of some 404 error, and also, I can't view most video on my browser (I can move the video to Mplayer). 
Any help would be greatly appreciated.

---

### Post by Hospadar on 2007-10-25
em, I would suspect that something is amok with your software sources.  You might try copying a new sources.list file off a fiesty cd, or see if you can locate one of the sample files on your system.

If you choose to go this route **Back up the old one**  I really don't know how well this will work.  but if you back up the old one, I would imagine you'd be fine.  You'd probably need to re-enable universe and multiverse after copying in the new file.

You can search your machine for sample sources.list files.  I happen to have one at /usr/share/doc/apt/examples/sources.list and another at /usr/share/ubuntu-docs/ubuntu/sample/sources.list

The real sources.list file is located at /etc/apt/sources.list, so copy in the new one there.  You'll need to use "sudo" to do the copying, or open a nautilus window as root with (from command line) "gksu nautilus"

If you copied with the command line, you would probably want to do something like this ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.my_backup
sudo cp /usr/share/doc/apt/examples/sources.list /etc/apt/sources.list
```The first line to back up the old file, the second line to copy in the new one (if you have to get the file from the livecd or a different location, you'll have to change the second command appropriately)

Just in case you don't know, the sources.list file is where apt gets it software sources from.

If none of this nonsense works, you can always just back up your home directory and do a clean install of 7.10 (that's what I did)

**Edit: please back up important things before you do this, I'd hate to be the reason you loose important work.**

---

### Post by CheshireMac on 2007-10-25
Hmmm . . .okay. I tried doing that, and I also went through Update Manager to update a small Thunderbird update. When I did this it told me I could only do a partial upgrade. When I said okay, it then failed to do so, saying it could not install 'ubuntu-desktop'. The message following that is to include 'var/log/dist-upgrade/' in the bug report. Weird. Anyhow, I was curious about this, and I'm going to research it right after this post.

---

