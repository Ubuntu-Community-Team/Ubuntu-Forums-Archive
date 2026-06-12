---
title: "Can't get rid of stupid locked directory on Desktop [Resolved]"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by elaich on 2007-03-04
There is a locked directory on my user desktop that I cannot get rid of. It's left over from a failed installation. 

I opened a terminal as root, cd'd to the Desktop, and tried every command I could find to erase it. It's still there.

chmod u+x  - permissions did not change

chmod o+x, chmod o+w - permissions did not change.

rmdir --ignore-fail-on-non-empty  - no messsages but directory still there

rmdir - directory not empty

There has got to be an easy way, isn't there? I remember going through this years ago in DOS, looking through piles and piles of directory trees to find the one file that was stopping the deletion.

---

### Post by maniacmusician on 2007-03-04
> **elaich said:**
> There is a locked directory on my user desktop that I cannot get rid of. It's left over from a failed installation. 

I opened a terminal as root, cd'd to the Desktop, and tried every command I could find to erase it. It's still there.

chmod u+x  - permissions did not change

chmod o+x, chmod o+w - permissions did not change.

rmdir --ignore-fail-on-non-empty  - no messsages but directory still there

rmdir - directory not empty

There has got to be an easy way, isn't there? I remember going through this years ago in DOS, looking through piles and piles of directory trees to find the one file that was stopping the deletion.
easy way = formatting the partition.

can't really think of anything else that you haven't tried already.

---

### Post by elaich on 2007-03-04
I don't understand why the permissions won't change.  If root is the owner, and I am logged in to terminal as root, I should be able to change them. But they refuse to change. I could simply send the directory to trash if user has execute privileges, right? It's got me pulling my hair out.

---

### Post by elaich on 2007-03-04
Sometimes, the answer is right in front of your face..... :lolflag: 

sudo nautilus

Move to trash. ):P

---

### Post by ComplexNumber on 2007-03-04
whats the directory called? if it is a link to anything, what does it link to?

EDIT: too late. the problem seems to be solved.

---

### Post by elaich on 2007-03-04
It's solved, but I still want to know why root couldn't change the permissions. There's something weird about that.

---

### Post by aysiu on 2007-03-04
> **ComplexNumber said:**
> whats the directory called? if it is a link to anything, what does it link to?

EDIT: too late. the problem seems to be solved.
Or, better yet, *gksudo nautilus*

---

### Post by aysiu on 2007-03-04
> **elaich said:**
> It's solved, but I still want to know why root couldn't change the permissions. There's something weird about that.
I think to make a *chmod* work on a folder, you have to make it recursive: ```
sudo chmod -R 775 *nameoffolder*
``` for example.

---

