---
title: "Transfer Win XP Thunderbird 2.0 Profile to Ubuntu 7.04, Thunderbird v1.5"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by CamanoAlan on 2007-05-16
Reading  various Thunderbird and Ubuntu forums it appears that the recommended procedure is to move certain folders and/or files from  Windows XP Thunderbird into the Ubuntu 7.04 Thunderbird profile. Simple right?

I've tried placing the entire Win XP profile into 7.04.mozilla-thunderbird folder with corresponding update of the profiles.ini file pointing to the new xxxxxx.default file name which resulted in a "Mozilla-Thunderbird is already running but is not responding. . ." message. 

I then tried individual folders from the XP Profile placing then first into the Mail sub-folder and then into the Local Folders sub-folder of the Ubuntu Profile. 

All I see in Ubuntu 7.04, Thunderbird 1.5 is the default Local Folders list created with a new account. I'm stumped. Suggestions are welcome and appreciated.

Thanks, Alan

---

### Post by rsambuca on 2007-05-16
I have found it is easiest to share the thunderbird files and folders on a FAT32 partition I created.  I also share a common firefox profile as well.  This way, whether I boot into XP, Vista, ubuntu, or any of my other OS's they all use the same profiles.  My mail is accessible from all OS's and my firefox cookies, bookmarks, history, etc are also shared.

With Thunderbird, all I did was put a folder called 'thunderbird' on the FAT32 partition,  I created my account (happened to be in XP at the time), and then set everything up the way I wanted.  I then booted into each of the other OS's on my rig and just pointed the local mail directory to the same location (under edit - account settings).

---

### Post by SirSpammenot on 2007-05-24
rsambuca has it.  Each OS maintains it's own Thunderbird profile directory.  The /Mail directory can be accessed from any OS, but the extensions can(!) be and paths are(!) OS specific.

Look in each profile at prefs.js and you'll see the paths under server1.blahblah.
So YES you can copy the profile directory from Suse to Ubuntu (same OS+pathing) but not from a Win32 box to linux.

I share my TB mail across various systems/OSes - it is great!  Just be aware you have to hand modify the path to the mail folder.

---

### Post by scampisi on 2007-06-28
I have followed the insturctions above and have now shared my profile for my thunderbird between my two OS's (Wind Xp Pro and Ubuntu 7.04).  This works fine when I check my email from Windows, or Ubuntu, but once I check the mail from Windows and try and reboot into Ubuntu to check mymail again, it gives me this error
"mozilla-thunderbird is already running but is not responding" 

It tells me to close thunderbird and try again.  Obviously thunderbird isn't still open.  If I create a new profile in Ubuntu, and point it to my shared profiles folder, I can read my email just fine.  Everything works fine until I boot into windows and check my mail from there.  Once I've done that, I have to re-create a profile the next time I check my mail from Ubuntu.

Any ideas?

---

