---
title: "Login error message $home/.drmc"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by red_Marvin on 2005-10-16
After upgrading to breezy one of the users get an error message at login saying:
> Your $HOME/.drmc file has incorrect permissions and is being ignored. This prevents the session from being saved. File should be owned by user and have 644 permissions.
Now, wether I try with console or nautilus I can't find that file, so I simply wonder
what I should do next to rid myself of the problem?

---

### Post by SilentCacophony on 2005-10-16
Hi. Not sure if you know that's a hidden file or not, so: if you open a terminal as that user, it should start you in the ~/ directory (home) for that user. if you issue

ls -la

it should show all hidden files and thier permissions and owners.

Sounds as if you somehow got userids messed up, so the problem could be more extensive than that one file. I've never had such a problem, myself, so I don't know how you'd sort that out.

---

### Post by red_Marvin on 2005-10-16
Well I pressed ctrl+H in nautilus, so hidden files should be shown, but no trace
of that one. In my own $HOME I did find the file, and tho only thing it said was:
> [Desktop]
Session=default

It seems quite unspecific, so perhaps I could just copy it to the other users $HOME...

---

### Post by ThirdWorld on 2005-10-16
I have exactly the same problem after I download win32 video codecs, and update the pakage manager. Now totem plays .wma and other type of video files, and real player stream radio in firefox (still no video in firefox thougth)  When I log in ubuntu I getting exactly the same error message, it looks to me is an ubuntu bug: 

"Your $HOME/.drmc file has incorrect permissions and is being ignored. This prevents the session from being saved. File should be owned by user and have 644 permissions." 

any sugestions?

---

### Post by chaumurky on 2005-10-16
Yup, I got that too. Quite a pain when you're wanting to VNC from somewhere else and this silly huccup stops the show...

---

### Post by superultra on 2005-11-09
I am getting this as well.  Anyone figure out how to fix it?

---

### Post by Kyral on 2005-11-09
[http://www.ubuntuforums.org/showthread.php?p=479186#post479186](http://www.ubuntuforums.org/showthread.php?p=479186#post479186)

This guy seems to have fixed it

---

