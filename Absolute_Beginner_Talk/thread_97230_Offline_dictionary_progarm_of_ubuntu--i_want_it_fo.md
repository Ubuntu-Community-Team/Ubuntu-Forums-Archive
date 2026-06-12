---
title: "Offline dictionary progarm of ubuntu--i want it for Mandrake"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by billubuntu on 2005-11-30
Hi,
i am actually a mandriva user.i desperately need a OFFLINE dictionary program for linux(similar to babylon of windows)
i heard Ubuntu gives users an in-built dictionary program.i want to know its name and where can i get that?will it work at mandrake?i have an ubuntu live cd  will that program available in its repository?
plz advice.
:)

---

### Post by kairu0 on 2005-12-01
I use stardict. I haven't found dictionaries for it as thorough as those for Babylon, though.

---

### Post by hassan_saeed on 2006-11-15
[SIZE="3"]
I was very happy to see i can use wine to install and run wordweb dictionary free version.[/SIZE]
the dictionary can be downloaded from:
 
[http://wordweb.info/free/]("http://wordweb.info/free/")

An .exe file in the install directory named _wwnotray.exe_ can be run using wine after the program has been installed.

This has solved my problem for having a good dictionary ofline.

---

### Post by mandar-seo on 2006-11-28
From where to get Wine and how to install it to Ubuntu? I am newbie and has never used the Linux before. Any help?

With regards,
Mandar Thosar

---

### Post by daller on 2006-11-28
> **mandar-seo said:**
> From where to get Wine and how to install it to Ubuntu? I am newbie and has never used the Linux before. Any help?

With regards,
Mandar Thosar

Go to a terminal, and run this command:

```
sudo aptitude install wine
```

Is this for wordweb?

Please don't hesitate to ask for help!

---

### Post by go_beep_yourself on 2008-05-08
Is there some way to port the dictionary from wordweb to a native Linux program? I'm about to give wordweb a try.

---

### Post by AdamWill on 2008-05-09
You could try 'stardict', it seems quite comprehensive.

---

### Post by go_beep_yourself on 2008-05-09
> **AdamWill said:**
> You could try 'stardict', it seems quite comprehensive.

I am using it now because it works with the converted Babylon dictionaries. I've got 3 issues with it though. See if you can help with the first two please.

[LIST=1]
[*]Can't remove the included Chinese dictionary. Because the author is Chinese, he seems to want to make everyone learn Chinese. I tried all the standard ways and looked in other places.
[*]The scan option turns off by itself after using it about 5x.
[*]The advertisements make it like a commercial windoze application. I'm going to recompile with a --no-advertisement option. Check ./configure --help. I don't need help with this one.
[/LIST]

---

### Post by matheweugene on 2008-05-23
> **go_beep_yourself said:**
> I am using it now because it works with the converted Babylon dictionaries. I've got 3 issues with it though. See if you can help with the first two please.

[LIST=1]
[*]Can't remove the included Chinese dictionary. Because the author is Chinese, he seems to want to make everyone learn Chinese. I tried all the standard ways and looked in other places.
[*]The scan option turns off by itself after using it about 5x.
[*]The advertisements make it like a commercial windoze application. I'm going to recompile with a --no-advertisement option. Check ./configure --help. I don't need help with this one.
[/LIST]

I was able to remove the Chinese in stardict by registering for the network dictionary, and then choosing a different network dictionary. Doesn't use the superior babylon dictionary I have installed offline though, which is annoying, but I can still access it by opening the word in the main program after mouse selecting it.

---

### Post by AdamWill on 2008-05-23
Thanks for the pointer on the advertisement disabling option: I've put that into the Cooker build now and I'll send it as an update for 2008.1 too.

---

