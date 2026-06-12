---
title: "Screwed up Automatix2 install-help"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Real Newbie on 2007-02-09
I am installing Automatix in Edgy Xbuntu.
I use the following commands
```

echo “deb http://www.getautomatix.com/apt edgy main” | sudo tee -a /etc/apt/sources.list

wget http://www.getautomatix.com/apt/key.gpg.asc

gpg --import key.gpg.asc

gpg --export --armor 521A9C7C | sudo apt-key add -
```

My last command is 

```
kelly@xbuntu:~$ sudo apt-get update

E: Type ‘“deb’ is not known on line 40 in source list /etc/apt/sources.list
```

I realized that I screwed up. I tried to run the update manager and it will only open for a sec and then closes back down. I rebooted and the resolution on my screen changed and I can't get the update to work.

Advice?

Noob



What do I do?

---

### Post by dbbolton on 2007-02-09
open /etc/apt/sources.list with gedit and see what line 40 says.

---

### Post by Real Newbie on 2007-02-09
How do I 

"open /etc/apt/sources.list with gedit and see what line 40 says."

Thanks,
Noob

---

### Post by Happy_Man on 2007-02-09
type the following code into your terminal:

```

sudo gedit /etc/apt/sources.list

```

---

### Post by Real Newbie on 2007-02-09
I did that and recieved

```
kelly@xbuntu:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
```

This is edgy in Xbuntu.

Thanks,
Noob

---

### Post by shareMenaPeace on 2007-02-09
use 
```
gksudo gedit 
```

---

### Post by Maestro23 on 2007-02-09
If you are running Xubuntu, you probably don't have gedit installed.  You will have to enable extra repositories.  How to is [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

In Xubuntu I use either vi, vim, or nano.

Nano is more user friendly.

#sudo nano -B /etc/apt/sources.list

-B makes a backup copy of the file for you before you edit it.

---

### Post by Real Newbie on 2007-02-09
```
kelly@xbuntu:~$ gksudo gedit
sudo: gedit: command not found
```

What now?

Noob

---

### Post by Maestro23 on 2007-02-09
> **Real Newbie said:**
> ```
kelly@xbuntu:~$ gksudo gedit
sudo: gedit: command not found
```

What now?

Noob

See my post above.

---

### Post by Happy_Man on 2007-02-09
I believe in Xubuntu, you have a text editor called Mousepad. Try

```

sudo mousepad /etc/apt/sources.list

```

and see what happens.

---

### Post by Maestro23 on 2007-02-09
> **Happy_Man said:**
> I believe in Xubuntu, you have a text editor called Mousepad. Try

```

sudo mousepad /etc/apt/sources.list

```

and see what happens.

Good catch Happy...I forgot about that one.:)

---

### Post by Real Newbie on 2007-02-10
All,
Thanks for your help. Apparently, when I used the command
```

echo “deb http://www.getautomatix.com/apt edgy main” | sudo tee -a /etc/apt/sources.list
```

The line kept the quotation marks. Once I removed these it ran like a charm. Thanks for all of the help. This is the reason that I have chosen Ubuntu. There is always great help available.

Thanks Again,
Noob

---

### Post by lanchongzi on 2007-02-10
hi I am trying the same : getting automatix2 to run under Xubuntu
i do as you guys say what i get is:

--00:40:00--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... failed: Connection timed out.
Retrying.



the terminal tries it seven or so times and then i admit that sth is wrong.
But what is wrong?
it seemed to have worked for you guys???:confused:



and this is the terminal:

lanchongzi@lanchongzi-desktop:~$ echo deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main | sudo tee -a /etc/apt/sources.list
Password:
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
lanchongzi@lanchongzi-desktop:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--00:45:00--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... failed: Connection timed out.
Retrying.

---

### Post by Real Newbie on 2007-02-10
I am definetly not the person that can solve your problems. I am still trying to teach myself LINUX.

However it says that your connection timed out. Doesn't this point to your internet connection or the web site and not the commands that you used?

Also this is the link that I used to install ([http://www.debianadmin.com/install-automatix2-in-ubuntukubuntuxubuntu.html](http://www.debianadmin.com/install-automatix2-in-ubuntukubuntuxubuntu.html)) Be extremely careful. There is one of the commands that have quotes surrounding part of the command and they should be deleted. Also make sure you are using the instructions for your correct ver Dapper or Edgy.

My $0.02, hope it helps. 1st time I have tried to help someone as so many have tried to help me over the last 2 months.

Good Luck,
Noob

---

### Post by lanchongzi on 2007-02-10
hihi  yes the quotation marks...

 I figured them out before i posted this ( but just because it was writen in this, or was it another thread - lost count :)  )
but thanks for your nice help though.
now it is 9.00 in the morning  ( I am in China :-D  )
so I am gonna try your link:)

thanks again for you and all the other patient people here in this forum

it is because of people like you that I dont miss Windows

lanchongzi


Edit:  i just tried it again ( btw I used your link ) with the same result.
the frustrating thing is that it was done 12 or so hours ago....
it may be because of the f***** up connection we get in China


is there another way??

like maybe inputing their website in the synaptic menu and then just run the synaptic manager???

---

