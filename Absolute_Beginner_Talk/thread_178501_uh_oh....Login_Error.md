---
title: "uh oh....Login Error"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by stansz on 2006-05-17
When i try to login, i get this::


GDM could not write to you authorization file.  This could mean taht you are out of space or that your home directory could not be opened for writing.  In any cause, it is not possible to log in.  Please contact your system administrator.


how do i fix it!!! 

plz help and thanks

---

### Post by Mustard on 2006-05-17
Hmmm..interesting situation.  I'd be curious if you could get to a root prompt using the 'Recovery mode' option in your grub menu.  From that root prompt you may be able to find out what it taking up all the space and delete a few files (assuming the error is caused by the first option 'out of space').

Do you have a live CD of some kind?

There are a number of threads around the forum where people have encountered this problem before, and in those threads there were commands suggested that can tell you which files are taking up the most space.  Probably the easiest ones to clear out are the packages that you download and install in the /var/cache/apt/archives folder.  Normally you can clear these out with an apt-get clean command.

If the problem is option 2. in the error message, a 'read only' filesystem, then it could be that there are errors on your partition somewhere and the filesystem has been mounted as read only due to these errors.  If this is the case then you might need to get a live CD and run the fsck command from there to check your filesystem for errors.  I suspect that its more likely that option 1. 'out of space' is the problem.

---

### Post by Sef on 2006-05-17
> Normally you can clear these out with an apt-get claan command.

do you mean apt-get clean command?

To clean up, from the command line:

sudo apt-get clean

sudo apt-get autoclean

---

### Post by Mustard on 2006-05-17
[QUOTE=Sef]do you mean apt-get clean command?

To clean up, from the command line:

sudo apt-get clean

sudo apt-get autoclean[/QUOTE]
Yeah, I just spent the last 15 minutes hitting the 'edit' button trying to fix my typo, but the forum is being a bit flaky today. :)

---

### Post by xtacocorex on 2006-05-17
I think this has something to do with the .ICEauthority file in his home directory, but I could be wrong. I remember something similiar happening to me quite a while ago which is why I can't fully remember how I got rid of it.

---

### Post by Mustard on 2006-05-18
[QUOTE=xtacocorex]I think this has something to do with the .ICEauthority file in his home directory, but I could be wrong. I remember something similiar happening to me quite a while ago which is why I can't fully remember how I got rid of it.[/QUOTE]

It could be that too, but the symptoms of this problem sound a bit different,  If it is though it would be worth checking if the .ICEauthority and .Xauthority files in $HOME are owned by root or the user.  If they are owned by root, then you can delete them both from a root prompt (which you can get to in Recovery Mode), and that should fix the problem.

---

### Post by Mr Fat Bat on 2006-05-18
2 cents:

I had the exact same problem when I had set my /usr/home directory to that of a mounted fat32 win partition.

Are you using a mounted partition as your home directory?

---

