---
title: "IE for firefox?"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by qdvubun on 2006-07-19
how can I view website that require Internet explorer with firefox? I looked for IE tab for firefox extension but it said not available for linux. Is there another way? I dont want to install IE with wine.

2nd question:
how to open a port with firestarter

and last question is how to increase the waiting for respond during dual boot, Sometime I didn't even have enough time to pick which OS I want to boot.

Thanks

---

### Post by aysiu on 2006-07-19
You can try the User Agent Switcher extension.

If that doesn't work, you may have to install IE with Wine (IEs4Linux will help you with that).

For the timeout, ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` Find the line (toward the top) that says *timeout 5* and change *5* to whatever you want--*10* or *15* then save (Control-X, Y, Enter).

---

### Post by qdvubun on 2006-07-19
ok, I really like the IE tab extension, hopefully it will be available for linux someday.

---

### Post by chickengirl on 2006-07-19
> **qdvubun said:**
> ok, I really like the IE tab extension, hopefully it will be available for linux someday.
Unfortunately, that will not happen unless IE's engine goes open source or gets completely reverse-engineered or something, because IEtab depends on the IE installation already present on your computer (which is why it's windows-only).

---

### Post by Kilz on 2006-07-19
One thing Linux dose not need is IE running. It is one giant security flaw. There is no safe way to run it. Even if you install it on Linux with Wine only use it for the 1 or 2 sites that you absolutely cant use firefox with. Do not use it to surf with.

---

### Post by byen on 2006-07-19
In my experience, when you use the User Agent Switcher extension for firefox.. most sites work without any issues. But if the site you need to visit does need an IE, I think your only option would be to run the Internet Explorer via Wine. Sad... but there are no two ways around it.
Good luck!
byen

---

### Post by SonicChao on 2006-07-19
Exactly....I typically don't go to a lot of websites that require IE, but the security flaws that are bad on Windows, *and this is only a theory* could be worse for Linux, (example: It could affect your drive in a way that is supposed to spy on Windows, but corrupts your Linux install)

Also, don't believe what Wine tells you, it is slower then anything...>.>

---

### Post by NT4usB on 2006-07-19
Send a nastygram (well, a polite note really) to the webmaster and explain how you'd really like to visit his site (and his sponsors sites) but his Internet Exploiter coded pages won't work in Firefox. 
You can check if it's crap coding here:
[http://validator.w3.org/]("http://validator.w3.org/")
And send it along...
Believe it or not, one of the fishing websites I like to visit actually fixed their coding after I sent them an email. (well, maybe others emailed them as well.)
Point is, If they don't hear from us, they won't know they even have a problem.

---

### Post by KFASheldon on 2006-07-19
And if you do need IE6 then search out the script IES4LINUX runs very smothly, the web page has a lot of help and is clear and it install flash too.

Dont know if it me but IE6 installed like this is much faster than any other web browser I have ever used Win or Linux - side effect would apear to be a little flickery screen update but it is fast.

On subject of spyware and such my guess is it just wont find what it wants as it not on a win machine, a lot of the things it might try to effect will only effect a heavily installed wine set uo I guess and are unlilkely to work out in the Linux domain. But brings to mind if there is any protection offered by wine ?

---

### Post by Kilz on 2006-07-19
> **KFASheldon said:**
> And if you do need IE6 then search out the script IES4LINUX runs very smothly, the web page has a lot of help and is clear and it install flash too.

Dont know if it me but IE6 installed like this is much faster than any other web browser I have ever used Win or Linux - side effect would apear to be a little flickery screen update but it is fast.

On subject of spyware and such my guess is it just wont find what it wants as it not on a win machine, a lot of the things it might try to effect will only effect a heavily installed wine set uo I guess and are unlilkely to work out in the Linux domain. But brings to mind if there is any protection offered by wine ?
Wine is a bug for bug windows emulator. If there is a windows flaw count on it effecting wine unless you know for a fact it doesnt.

---

