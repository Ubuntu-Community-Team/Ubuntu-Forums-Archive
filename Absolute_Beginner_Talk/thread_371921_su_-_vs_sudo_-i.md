---
title: "su - vs sudo -i"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by brundles on 2007-02-27
Hope someone can help me with this - it's beginning to annoy me a bit :(

From looking at the man pages, sudo -i -u should run a command as the given user having done an initial login for the duration of the command. As I see it, this means it should be the same as doing:
   su - keith
 
Then running the command.

Unfortunately, vnc4server refuses to behave. The following works:
su - keith
vnc4server

This doesn't, instead complaining about tokens from within the vnc4server script.
sudo -i -u keith vnc4server

Hope someone can help with this.

Thanks,
Keith

---

### Post by ciscosurfer on 2007-02-27
> **brundles said:**
> Hope someone can help me with this - it's beginning to annoy me a bit :(

From looking at the man pages, sudo -i -u should run a command as the given user having done an initial login for the duration of the command. As I see it, this means it should be the same as doing:
   su - keith
 
Then running the command.

Unfortunately, vnc4server refuses to behave. The following works:
su - keith
vnc4server

This doesn't, instead complaining about tokens from within the vnc4server script.
sudo -i -u keith vnc4server

Hope someone can help with this.

Thanks,
KeithThis wiki page might shed some light on the whole su vs sudo issue for you >> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 
And this is also a good read >> [http://www.radiotope.com/writing/?p=56](http://www.radiotope.com/writing/?p=56) 
As well as here >> [http://www.tuxmagazine.com/node/1000148/print](http://www.tuxmagazine.com/node/1000148/print) 
And here >> [http://www.linuxquestions.org/questions/showthread.php?t=526532](http://www.linuxquestions.org/questions/showthread.php?t=526532) 
And finally >> [http://ubuntuforums.org/showthread.php?t=53575](http://ubuntuforums.org/showthread.php?t=53575).

---

### Post by brundles on 2007-02-27
Excellent - that tells me what I needed to solve the problem :)

Thanks very much!

---

### Post by kittyhawk63 on 2007-02-27
> **brundles said:**
> Excellent - that tells me what I needed to solve the problem :)

Thanks very much!

Brundles,
If your problem is resolved, you should mark it as resolved. Start to edit your original post and then choose Advance Edit. You will be given some choices near the top of the page. "Mark as Resolved or as Unresolved." It saves people from looking to help you and those with similar issues can look at your post for suggestions.
Gud daay!

---

