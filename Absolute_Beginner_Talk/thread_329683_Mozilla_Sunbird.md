---
title: "Mozilla Sunbird"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Quillz on 2007-01-02
I want to use Mozilla Sunbird 0.3, so I downloaded a [FONT=Courier New]sunbird-0.3.en-US.linux-i686.tar.bz2[/FONT] file, which I extracted to the [FONT=Courier New]/usr/mozilla/[/FONT] directory. Now there is a folder in there called "[FONT=Courier New]sunbird[/FONT]" with a lot of files, but I don't know what to do next. How do I install and use Sunbird, or am I already done? If so, what file(s) do I need to run?

---

### Post by seijuro on 2007-01-02
you just need to run the binary file it may have .bin or it could be an .sh script to start up or if I remember correctly it is simply sunbird. what you do is go into the sunbird directory and type ./sunbird you can create a link in /usr/bin so that you can just type sunbird in the console or you can manually add it to a menu or create a launcher. To make the link in /usr/bin go to /usr/bin and type "sudo ln -s /usr/mozilla/sunbird/sunbird ."

like the avatar btw :)

---

### Post by Quillz on 2007-01-02
It says that I need to enter a password in the Terminal, but when I try to type it, nothing happens.

---

### Post by seijuro on 2007-01-02
passwords are not echoed in linux for security trust me it is typing the password just hit enter after you finish typing. It confused my dad too so don't feel bad.

---

### Post by Quillz on 2007-01-02
> **seijuro said:**
> passwords are not echoed in linux for security trust me it is typing the password just hit enter after you finish typing. It confused my dad too so don't feel bad.
You're right! It did work after all. Thanks for all of your help. I now have Sunbird installed and am making great use of it.

---

### Post by b1g4L on 2007-01-15
This also worked for me with Sunbird 0.3 on Edgy. Thanks seijuro! Any reason sunbird is not in the repos?

---

