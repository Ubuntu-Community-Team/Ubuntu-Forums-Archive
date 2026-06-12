---
title: "One music folder, two OSes"
date: 2007-11-19
forum: Apple Intel Users
---

### Post by Seamyst on 2007-11-19
I have three partitions on my MacBook CD - Tiger, Gutsy, and a shared partition.  I would like to be able to have all my music on the shared partition and have both iTunes and Banshee/Rhythmbox play from that one set of music.  Preferably I would like to set it up so that I put a song in the proper folder, and then whichever music player I open up would be able to automatically import that song for me to put in a playlist.

Is this possible?  If so, how would I go about setting this up?  I'm a relative newbie so I would need step-by-step instructions, but I'm comfortable doing almost anything as long as it's explained to me.

**Edit:**  Here's my partition scheme.  The shared partition is hfsplus and 25 gigs in size.  The Tiger partition is also hfsplus and 10 gigs.  The Gutsy partition is ext3 and twenty gigs.  I'd really like to put the music folder in the shared partition, since it has the most space available.

---

### Post by hardyn on 2007-11-19
i am doing it windows/linux via a fat32 parition that is common to both OSs.  I believe that linux can negotiate an OSX filesystem (hfs?) so it should not be a problem at all, simply mount the OSX parition and everything should just work.

---

### Post by Seamyst on 2007-11-19
I can't get into the Music folder in the OSX partition from Gutsy.  I don't know why, I've checked half a dozen times and the permissions are correct... I put ```
/dev/sda2 /media/osx hfsplus user,ro,umask=0644 0 0
``` in fstab and fiddled around with it until the address and the umask matched the partition, but it didn't work.  (And I'm really paranoid about changing the uid, since the hard drive crashed a month after I did that.)

I'd also like to have the music folder in the shared partition, since the Tiger partition is small.

---

### Post by atlascomplete on 2007-11-19
It also depends on how you partition is also. Using a FAT32 partition will not let you do this, but using a NTFS partition will.

---

### Post by Seamyst on 2007-11-19
Sorry - I updated the first post with more information.

---

### Post by cyberdork33 on 2007-11-19
you cannot mount a journaled hfs+ drive in linux... also there are permissions issues that you cannot work around.

[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

---

### Post by tgalati4 on 2007-11-20
Just turn off journaling in the hfs partition where your music resides.  You can do this using the "erase" function and changing the volume type with mac's Disk Utility.

(You need to do this to Mac-formatted iPods as well so you can write to them with gtkpod.)

You can also use an ext2 or ext3 partition and Mac can read and write to it.

Banshee won't automatically update a music library.  You have to manually import it and you will get errors reported about duplicate songs.  They won't get imported, but you will have to  update manually.  Other players have autoupdate which is nice.  I don't know why this has not been implemented in Banshee yet.

Some helpful info:

[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

---

