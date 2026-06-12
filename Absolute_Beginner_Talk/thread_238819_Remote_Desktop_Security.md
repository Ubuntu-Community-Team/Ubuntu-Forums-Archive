---
title: "Remote Desktop Security"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by paul_h on 2006-08-18
I am a very happy new Ubuntu user. Applications I have already running on Ubuntu do everything I need, apart from video editing and printing photo quality on my Canon ip4000 (colours not 100 per cent).

I have used Remote Desktop very successfully, but I cannot find any documentation that describes any security features of Remote Desktop. Is documentation on such detail available?

---

### Post by &#12465;&#12452;&#12488; on 2006-08-18
By remote desktop, do you mean by using the VNC protocol? Then you can tunnel the traffic trough SSH. If you refer to using RDP to communicate with Windows computers, I have no idea.

---

### Post by paul_h on 2006-08-18
No, I'm not referring to VNC, but rather to the Remote Desktop within Ubuntu ... System / Preferences / Remote Desktop.

I have only used it with another Ubuntu user over broadband and it worked very well.

---

### Post by bluefrog on 2006-08-18
it's using vnc. So your password ships in clear thru the network.

search the wiki to understand how to use ssh and vnc altogether.

James

---

### Post by &#12465;&#12452;&#12488; on 2006-08-18
Yeah, that is VNC, actually.

As I said, you can tunnel the traffic through SSH, then it will be encrypted. That, however, is a bit complicated. [Here's](http://z.cs.utexas.edu/users/habals/blog/index.php/linux/22) a website describing how to do it. You can also [search the forums](http://www.ubuntuforums.org/search.php?searchid=7548549), or maybe [Google has some answers](http://www.google.com/search?q=Ubuntu+VNC+SSH+tunneling&btnG=Search)!

---

### Post by paul_h on 2006-08-22
Thanks for the pointers.

I came across this gem that makes me feel reasonably relaxed about VNC security: "VNC uses a challenge-response password scheme to make the initial connection: the server sends a random series of bytes, which are encrypted using the password typed in, and then returned to the server, which checks them against the 'right' answer."

I'll look into tunneling through SSH.

Thanks again.

Paul.

---

