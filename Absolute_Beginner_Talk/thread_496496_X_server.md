---
title: "X server"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Agent47 on 2007-07-09
I have new problem. When I start my computer and trying to boot up I ll get error "failed to start X server" 
What I have to do now? How I can solve this problem`?

---

### Post by Sklasko on 2007-07-09
You'll need to reconfigure xorg.

Execute this from a terminal session:

```
sudo dpkg-reconfigure xserver-xorg
```

Someone correct me if I'm wrong. Hope this helps.

---

### Post by iUSER-Mike on 2007-07-09
Hello, don't now if rlevent. I just followed sticky for ATI cards, and rebooted and now stuck with Xserver can't start, Ive tried rebooting but the system replies the same and I can't get past "OK", the system hangs.

Can sudo dpkg-reconfigure xserver-xorg be typed in if I started in safe mode?

Cheers Mike:confused:

---

### Post by Sklasko on 2007-07-09
Yes, that would be a good way to access a terminal session to enter this command.

---

### Post by iUSER-Mike on 2007-07-09
Cheers Dude/Dudette:guitar:

Sklasko:KS

---

### Post by Agent47 on 2007-07-09
I really dont know what to do. I enter this comand line but what next i have to do ? there are no option config anything. All option I got ,--- anything I do can case serious malfunctions .etc And I m not very good at this comand line Im afraid to **** up things.

---

### Post by overdrank on 2007-07-09
> **Agent47 said:**
> I really dont know what to do. I enter this comand line but what next i have to do ? there are no option config anything. All option I got ,--- anything I do can case serious malfunctions .etc And I m not very good at this comand line Im afraid to **** up things.

Hi, if you do not know what make you graphics card is then just stick with the default given. Same will go for the others questions asked. If you dont know the answer just stick with the default given and once you are on the desktop gui then you can search for the drivers for you graphics card. Hope this helps good luck!

---

### Post by Fire Legion on 2007-07-09
I did that and it still doesn't work. Can anyone help me?

---

