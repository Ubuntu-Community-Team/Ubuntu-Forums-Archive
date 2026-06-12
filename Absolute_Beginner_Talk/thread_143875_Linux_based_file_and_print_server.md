---
title: "Linux based file and print server"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by jcherry117 on 2006-03-13
Please help. I have turned one of my old pc into a file and print server. I am able to access files from my windows pc to the linux machine and now I am wanting to be able to use it as a print server on my network. I am unable to figure out how to make the windows pc install a network printer that is connected to my linux machine. Please if you have any step by step instructions I would really apppreciate it
Jeff

---

### Post by Pragmatist on 2006-03-13
Check this out:
[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29)

---

### Post by jcherry117 on 2006-03-14
I am having trouble getting this to work for printing using my windows machine

---

### Post by Pragmatist on 2006-03-14
Well, SAMBA is the normal way, although in the near future I believe there will be a Window's driver which will make things easier. For more about that go to:
 [http://cups.org/windows/index.php]("http://cups.org/windows/index.php")
You can navigate the [http://cups.org]("http://cups.org") site for other info too. CUPS is the main print server software for Linux. From the cups.org site there is reference to a commercial product that should do what you want: [http://www.easysw.com/printpro/]("http://www.easysw.com/printpro/")

Finally, you might consider trying this free software:
[http://sourceforge.net/projects/cupsclient/]("http://sourceforge.net/projects/cupsclient/")

---

### Post by skirkpatrick on 2006-03-14
Is your Windows machine XP or 98?  I have my XP and 98 machines using my Linux machine to print.  I use Samba for the 98 machines and CUPS for the XP machine.  I can help you out with the methods I used.

---

