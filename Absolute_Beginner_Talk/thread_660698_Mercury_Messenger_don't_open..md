---
title: "Mercury Messenger don't open."
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by rhc on 2008-01-07
I installed mercury messenger and restarted the computer but when i m clicking the icon in applications,nothings happens.
Do i have to download something more for mercury to work?

---

### Post by rax_m on 2008-01-07
I had a quick look at the website and it seems mercury msger requires java to be installed.. Do you have it installed ?

Also, you can try opening a terminal window and executing the command for mercury msger in there. I don't know what this command is, but if you type merc (and press tab) it might help. Then you'll be able to see error msgs for why it doesn't work.

---

### Post by rhc on 2008-01-07
Yeah,i installed java and it s opening now.
But when i open it,from terminal or applications menu,mercury window appears but it is only white,no other word or something.
Then i open it from terminal to see the error and it s saying "loading splash screen",but it doesn't appear,i wait 5 minutes but it s still the same. Loading splash screen. And nothing else except the white screen in mercury window.

Just like below

[http://img229.imageshack.us/img229/1264/ekrangrntsvn1.png](http://img229.imageshack.us/img229/1264/ekrangrntsvn1.png)

---

### Post by rhc on 2008-01-07
No solution?

---

### Post by PmDematagoda on 2008-01-07
Post the output of:-
```
sudo update-alternatives --config java
```

---

### Post by rhc on 2008-01-07
I wrote last code and selected java,second one.
But the same appearance in mercury.
White only.
My java is 1.5.0 version i think.
I installed it from Synaptic.
Is that a problem about it?
Should i install a new one?
I downloaded 1.6 a file called "jre-6-linux-i586-rpm.bin" from Java but i could'n load it?
Maybe i installed mercury wrongly?

pff :(

---

### Post by PmDematagoda on 2008-01-07
Open the Synaptic Pakcage Manager and search for "jre", then install the sun-java-6 packages, after they are installed Mercury should work.

---

### Post by rhc on 2008-01-07
Thanks PmDematagoda,
It solved the problem.

---

