---
title: "Tip - Dual boot users share firefox bookmarks"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-01-06
I hope this is the right place for this little titbit. If not, please feel free to move it accordingly.

Iv seen a few posts about sharing Firefox bookmarks across a dual boot, and most rely on Firefox extensions or some non-local server. This doesn't, and its quite easy. (This can also be done for Opera - see below)

1)
In Windows create a folder somewhere and copy the Firefox bookmarks file into it. This is in the /home/user/.firefox folder on Ubuntu, and the firefox profile folder on Windows.

2)
Create a .js file in a notepad of some kind with the following line in it:
```
user_pref("browser.bookmarks.file", "<Full path to >bookmarks.html");
```

Note that in each case you should use the correct format for the "Full path to" section, relevant to the OS. In Ubuntu my path is "/home/max/Desktop/winshare/foxmarks/bookmarks.html". (Note that I have a link to this folder on my Ubuntu desktop!)

3)
Save this .js file into your profile folder. Note that in Ubuntu this folder is in the /home/user/.mozilla.... folder, whereas in Windows it is in the c:/docs&settings/user/application data/mozilla/firefox/profiles....

Thats it. When Firefox in either OS loads it loads the same bookmarks file.

To get the same effect in Opera you need to move the opera6.adr file into the shared folder as well, and edit the opera6.ini file. In Windows this is in the opera folder, in the profile sub folder and on Ubuntu its in the /home/user/.opera folder (NOT in the profile folder).

Edit the line that starts with "Hot List File Ver2" to show the correct path, and again the two installations are sharing the same bookmarks file.

Please note that Im very new to Ubuntu, so if this is in some way doing something wrong, please by all means let me know!

---

### Post by PeterJS on 2008-01-06
You can expand on this and share an entire profile between FF installs on dual boot systems using symlinks.

1) set up ntfs-config so that your windows drive will show up in a consistent place in your file system with read/write access.

2) Open up a terminal:
```

cd ~/.mozilla/firefox/
ln -s /media/*windows*/Documents\ and\ Settings/*User*/Application\ Data/Mozilla/Firefox/Profiles/*profile_name* .
gedit profiles.ini

```The last line of profile.ini should say
path=profile_name
change the profile name to the name of the windows profile you just linked in. Restart firefox and enjoy.

---

### Post by kellemes on 2008-01-06
Another method..

Simply copy the profile(folder) you want to share to a shared disk and from "the other os" call..
```
firefox -profilemanager
```
Now browse to the copied folder and you're done.

---

### Post by PeterJS on 2008-01-06
That works well for a one time thing, but if they're both linked to the same files on the disk, if you make changes to one profile (new bookmarks, extensions, etc) the change to the other OS will be immediate and automatic.

---

### Post by MaxVK on 2008-01-06
Whoa there Peter! All those slashes and backslashes in that code lost me a bit. :confused:

Could you spell out what you have done (In *real* simple terms). I like the idea of sharing the whole profile between OS's.

---

### Post by PeterJS on 2008-01-06
So windows handles directory names with spaces a bit more elegantly than linux. Which is good and bad, good in that it's easier to put spaces in file names, bad in that's not how every other OS handles it, and introduces weird quirks like this when trying to get things to work together.

that whole big long line there is the path of where firefox keeps it's profile in windows a condensed version would be:
```

ln -s location_of_windows_profile here

```In order to put spaces in file names under linux you need to put a \ in front of them. That's called and escape character and tells the system that the thing after it is the letter " " (weird idea, I know), and not a separator between things in a list. So the folder "Documents And Settings" becomes "Documents\ And\ Settings"

---

