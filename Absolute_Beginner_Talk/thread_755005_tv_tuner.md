---
title: "tv tuner"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by sameer.india on 2008-04-14
I have an integrated tv tuner.
Tell me a software which can make it work

---

### Post by Speedwiz7770 on 2008-04-14
Google MythTV, it's software meant to turn your pc into a tivo-like station

---

### Post by newlinux on 2008-04-14
what brand/model of tv tuner is it? Do you just want to watch TV or record and timeshift? This information will help us direct you to the right software for your situation.

---

### Post by hellomoto on 2008-04-14
I was going to start another thread on the same topic but one has already been started here so I will give it a go.

I have a  "Pinnacle DVB-T PCI Card" 

lspci shows:

```

00:0a.0 Multimedia controller: Pinnacle Systems Inc. Royal TS Function 1
00:0a.2 Multimedia controller: Pinnacle Systems Inc. Royal TS Function 3

```

All I require is to watch freeview TV, I don't want any bulky software as my comp isn't a high enough spec to cope with it, ( it was very slow when running on windows).

I heard that VLC Media player supports TV tuners. I have down loaded it but don't know how to go about getting my card to work and getting the drivers to work.

any help please?

---

### Post by halitech on 2008-04-14
have you tried TvTime? Pretty sure its in the repos and it is just a program to watch tv, won't record or anything like (unless someone can prove me wrong which I would love to have happen :) )

---

### Post by hellomoto on 2008-04-14
nope but more than happy to give it a go. Can i install it from synaptic package manager?

also what about installing the drivers for the card?

---

### Post by halitech on 2008-04-14
yes, tvtime is available in Synaptic

with LSPCI showing it, you may not have to install anything else. If Tvtime shows you a tv program, you are good to go.

---

### Post by hellomoto on 2008-04-14
ok installed TVtime and it once loaded i get the error

```

cannot open the capture device /dev/video0

```

any ideas?

---

### Post by halitech on 2008-04-14
Do you have a webcam hooked up as well? I know when I was setting up I had to disconnect my webcam to get things working

---

### Post by hellomoto on 2008-04-14
nope no webcam. doesn't look like my card is supported, is there any way i can check if its working?

---

### Post by halitech on 2008-04-14
there is a way of checking but I'm not home right now and I'm stuck on a windows box :( VLC will let you as well but I can't think of the code to use so I'll check this in about an hour or so when I get home and let you know

---

### Post by hellomoto on 2008-04-14
thank you :) im going to bed now anyway. I will have another go 2moro.

thank you for your help

---

### Post by sameer.india on 2008-04-15
Watch and record TV

---

