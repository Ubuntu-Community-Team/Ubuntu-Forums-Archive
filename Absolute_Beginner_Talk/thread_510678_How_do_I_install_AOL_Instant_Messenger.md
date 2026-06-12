---
title: "How do I install AOL Instant Messenger"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2007-07-26
My girlfriend has used Gaim and Pidgin, and doesn't like either.  On the aim website there is an aim for linux, and I was wondering if anyone can outline how to install it, because I tried following their instructions and it told me it was installed, I ran the command to run it, and got nothing.  So if anyone could outline how to install it I would really appreciate it.

---

### Post by buzzmandt on 2007-07-26
go to home folder and select view>show hidden files

see if there is an aol or similar folder, if so, open it, and find the executable, it should run from there

---

### Post by Sayers on 2007-07-26
That's pretty sad, she probably didn't give it a chance

---

### Post by buzzmandt on 2007-07-26
i agree, i always liked gaim, haven't im'd in a long time so haven't tried pigdin but most of what i read it's even better

---

### Post by Sayers on 2007-07-26
Pidgin from what I've seen just looks better.

---

### Post by dangerpl on 2007-07-26
AIM for Linux is an abandoned project and it doesn't come close to Gaim...If I'm not mistaken it's still a beta? You can try Kopete, or as others pointed out Pidgin... Gaim is much simpler than the new version of AIM and i know it's a bit frustrating with file transfers, direct connections and unfortunatelly it doesn't support video chat but hopefully it will be improved...

---

### Post by Specter043 on 2007-07-26
She says she doesn't care about anyone else's opinion, she gave it a whole half hour.  So does anyone know how to install it?  I know it's crappy, and I know the transfer, and the talk or whatever, and it's got those stupid ads, but it's either this or I use windows because she refuses to use gaim or pidgin.

---

### Post by dangerpl on 2007-07-26
lol being whipped a bit? how about a dual boot? so she can use windows and you can use linux?

---

### Post by FleetAdmiral74 on 2007-07-26
I think Pidgin should be in the repos for Gutsy, which I am looking forward to. Can anyone confirm or deny this?

---

### Post by Sayers on 2007-07-26
I can confirm it. It comes pre-installed.

---

### Post by Modernity on 2007-07-26
Here is one she might want to try, not sure if she will like it, but you can give ti a shot.
[http://www.licq.org](http://www.licq.org)

I feel for ya, I had to keep a whole Windows box for my wife becuase she refuses to use Linux, maybe someday i can convert her, we'll see. But keep trying and be patient with her.

---

### Post by Armman on 2007-07-26
The only real difference is the interface, she just needs some time to figure out what is where.

---

### Post by Specter043 on 2007-07-27
So I take it no one knows?  If nobody really does know, can anyone tell me how to get aim going in Wine?

---

### Post by Espreon on 2007-07-27
ZOMG, why does your girlfriend hate Gaim/Pidgen and does not accept the opinions of peeps. All I hafta say is to do the following inorder to get AIM working in Wine:

Fire up a terminal and enter:

```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

```

Then: ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
If it does not respond with and OK enter:

```
 wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg
```

If it did not give you an ok after the : sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list goto System>Administation>Software Sources and hit the Autentication Tab and hit import key and find the .gpg file we downloaded.

The enter the following in a terminal:

```
sudo apt-get install wine cabextract orange
```

Then enter this:

```
wget http://www.wine-doors.org/releases/wine-doors_0.1-1_all.deb
```

Replace "myhome" with the name of the home folder

Now enter this: ```
sudo dpkg --install  /home/myhome/wine-doors_0.1-1_all.deb
```

if that fails navigate to the .deb and install it by double-clicking it.

Now enter: ```
wine-doors
```

and enter your (if this your comp) or your girlfriend's name if you (if it is your comp) or your gf own/owned Winblows check the checkbox saying: Check if you Have a valid Windows(tm) license.

Now enter ```
wget http://download.newaol.com/aim/win95/Install_AIM.exe
``` to download AIM.

Now enter this ```
wine /home/myhome/Install_AIM.exe
```

If that does not work download the older version of AIM and enter ```
wine
``` in a terminal hit space and drag and drop the .exe of the older AIM. Install and it should appear in the Wine sub menu under Applications.

The Wine-Doors will be useful if she b****** about the lack of IE,WMP,DirectX and Winblows libraries as Wine-Doors will make it easy to install those under Wine.

---

