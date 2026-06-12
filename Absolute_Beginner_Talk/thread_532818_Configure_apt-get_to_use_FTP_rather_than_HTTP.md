---
title: "Configure apt-get to use FTP rather than HTTP?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by tigerplug on 2007-08-23
I can't use apt-get through HTTP and it would save me a whole lot of bother if I could configure it to use FTP.

I was just wondering is this possible? 
To the best of my knowledge, it is possible on Debian but I don't know about Ubuntu.

Can someone please advise me on this?
Detailed steps would also be appeciated.


Thanks :)

---

### Post by Bachstelze on 2007-08-23
Of course it is possible, you just need to change your sources.list so URLs begin with ftp:// rather than [http://.](http://.)

---

### Post by tigerplug on 2007-08-23
Where do I go to change this. Thats my problem. 

I assume its similar to a "Hosts" file that I can just fire up in a text editor?

I'm pretty new to Linux.

---

### Post by tribaal on 2007-08-23
You're looking for the /etc/apt/sources.list file.

This is the file where all repositories locations are stored (along with the URL). I strongly encourage to backup it before you modify it, as usual when editing system files.

Hope this helps...

- Trib'

---

### Post by tigerplug on 2007-08-23
Thanks for that!

---

