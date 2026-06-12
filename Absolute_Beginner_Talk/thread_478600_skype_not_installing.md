---
title: "skype not installing"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by kufio on 2007-06-19
Hi, I tried to install from repositories with synaptic. I am running Ubuntu Dapper but when I select it gives this response:

skype:
  Depende: libasound2 (>1.0.11) pero se va a instalar 1.0.10-2ubuntu4
  Depende: libc6 (>=2.4-1) pero se va a instalar 2.3.6-0ubuntu20.4
  Depende: libgcc1 (>=1:4.1.1-12) pero se va a instalar 1:4.0.3-1ubuntu5

Do you know if I can get this libraries updated? It seems that they are not supported under Dapper

---

### Post by Crafty Kisses on 2007-06-19
> **kufio said:**
> Hi, I tried to install from repositories with synaptic. I am running Ubuntu Dapper but when I select it gives this response:

skype:
  Depende: libasound2 (>1.0.11) pero se va a instalar 1.0.10-2ubuntu4
  Depende: libc6 (>=2.4-1) pero se va a instalar 2.3.6-0ubuntu20.4
  Depende: libgcc1 (>=1:4.1.1-12) pero se va a instalar 1:4.0.3-1ubuntu5

Do you know if I can get this libraries updated? It seems that they are not supported under Dapper

Try installing it manually from the command line.
```
sudo apt-get install skype
```

---

### Post by rigol on 2007-06-27
I don't know if you still need help on this one...

So you are trying to install Skype 1.4beta? This won't work for Dapper, it's a Feisty application. There is no other way than downgrading Skype to 1.3. 


My solution was the following: remove your Skype sources from your sources.list, Medibuntu has the old skype version still available. 

You can either add Medibuntu's repositories to your sorces.list and do a sudo aptitude update/ sudo install skype:
```

sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo aptitude update
sudo install skype
```

Or you can download it directly from here: [http://packages.medibuntu.org/pool/non-free/s/](http://packages.medibuntu.org/pool/non-free/s/) and install it manually.

Hope this helps.

---

### Post by moreinfo on 2008-05-31
Hi, so exactly... step by step... (sorry), how do I use Skype on Dapper... oh, and before you say why are you still using Dapper? well, I don't know how to change.. and I haven't the need too..

I'm just interested in getting skype set up again, I used too but then Ubuntu took it off, but we should be able to make a choice what we use.. secret code or not.. the thing is.. isn't it the same thing... anyway...
I just want skype, is someone able to lay it all out in lay terms.. nice and simple step by step..

Thanks in advance

P.S  I still have the icon in Apps --> Internet, but it just doesn't work.

---

