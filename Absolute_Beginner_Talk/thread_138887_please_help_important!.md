---
title: "please help important!"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by obey43 on 2006-03-02
i installed ubuntu on a partition and now windows wont start up

everytime i boot into windows

i get
"A problem is preventing windows From accurately
cheching the license for this computer Error code 0x80070002"

at the login screen...

everywhere on google did not fix my problem, 

i have no cryptology keys and mounted devices were right...

please help

---

### Post by mlind on 2006-03-02
MS has article about this on ther suppor & help
[http://support.microsoft.com/?kbid=310794](http://support.microsoft.com/?kbid=310794)

There seems to be steps included how to fix the problem.

---

### Post by obey43 on 2006-03-02
.	Delete the following registry keys in the Windows registry:
HKEY_USERS\.DEFAULT\Software\Microsoft\Cryptography\Providers
HKEY_USERS\S-1-5-20\Software\Microsoft\Cryptography\Providers


those two keys don't exist

and the mounted drive is correct 

(actually i changed it to incorrect and now windows doesnt boot at all)...

---

### Post by obey43 on 2006-03-02
which now adds a new question...

how can i edit the windows registry if i can't get into windows???

dang...

---

### Post by mlind on 2006-03-02
You can't access safe mode by hitting F8 on boottime?

You should also be able to access your registry using
xp's recovery console that's included on cd.

---

### Post by obey43 on 2006-03-02
nope because it thinks windows is now on a different drive because i changed it to say so in safe mode last time...

---

### Post by obey43 on 2006-03-02
what file do i edit and how from the registry cd
i have gotten there...
(i know this is sort of outside ubuntu discussion sorry)

---

### Post by mlind on 2006-03-02
I'm sorry but I can't help you on this, it's been a while since I've messed my
WinXP system. I mainly use Ubuntu. 

If you can't get on to safe mode, then you'll just have to find some other way
how to modify registry. I suggest you do your homework about windows'
registry before you go even near that beast. Maybe some external tool will
allow access to it if you don't know how to do it from recovery console.

Google may be your best aid on this.

---

