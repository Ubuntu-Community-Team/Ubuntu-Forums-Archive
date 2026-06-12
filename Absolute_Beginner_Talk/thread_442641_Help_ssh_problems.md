---
title: "Help ssh problems"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by tipalm73 on 2007-05-13
Im pulling my hair out!

I am running fiesty fawn. I installed changed openssh-server. set it to port 512 yadda yadda.

Then I had to reinstall and my problems began.

Now I cannot ssh back into machine cause i have wrong key.. ive reinstalled twice and it says same thing someone is middle man attacking you blah blah.

Im very frustrated

please help

---

### Post by wormser on 2007-05-13
You need to delete the ssh key.  I got these directions from this [post]("http://ubuntuforums.org/showthread.php?p=986843").

1. Edit the file ~/.ssh/known_hosts

2. Delete the entry of the computer that is not responding. Save and exit.

3. Try ssh again and it should ask you if you want to allow the remote box to connect. Say yes and it will write a new key to that file.

4. Should work at that point.

---

### Post by tipalm73 on 2007-05-13
Ahh! I was looking for known_hosts on the server not on the client machine.

I cleared out known_hosts on the client and it worked fine, thanks for the epiphany.

---

