---
title: "Packages Problem - Can't install/add repositories/applications"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by J.Byram on 2008-03-28
I JUST installed Gutsy Gibbon two days ago and I have never used it before.  I have been trying to install some new applications and I got some instructions from this website:
[CENTER]
[http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html](http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html)[/CENTER]

and they told me to do these commands:
 [CENTER]   ¨wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - ¨

and

    sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list"[/CENTER]

Now, when I try any sudo get-apt command in the terminal, I get this response from the terminal:
[CENTER]
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.[/CENTER]

Also, when I go into the Synaptic Package Manager, I get this error:

[CENTER]E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/CENTER]

And it automatically closes the manager box after I click "Close" on the error box. 

I have attached a screen shot of the issue. 

What should I do to remedy this?  And, how do I correctly install applications and repositories?  

Any suggestions for a newbie would be awesome.
Thanks,
John.

---

### Post by jkeyes0 on 2008-03-28
Try this command to get the correct sources.list file
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

More information on setting up medibuntu here
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Oldsoldier2003 on 2008-03-28
> **J.Byram said:**
> I JUST installed Gutsy Gibbon two days ago and I have never used it before.  I have been trying to install some new applications and I got some instructions from this website:
[CENTER]
[http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html](http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html)[/CENTER]

and they told me to do these commands:
 [CENTER]   ¨wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - ¨

and

    sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list"[/CENTER]

Now, when I try any sudo get-apt command in the terminal, I get this response from the terminal:
[CENTER]
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.[/CENTER]

Also, when I go into the Synaptic Package Manager, I get this error:

[CENTER]E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/CENTER]

And it automatically closes the manager box after I click "Close" on the error box. 

I have attached a screen shot of the issue. 

What should I do to remedy this?  And, how do I correctly install applications and repositories?  

Any suggestions for a newbie would be awesome.
Thanks,
John.

Once again that damn site botches an install. he really needs to fix/update that page...  : (

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```
Then System>Administration>Software Sources
Add  the first 4 repos then 
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by cisforcojo on 2008-03-28
I'm not sure about the DOCTYPE error but you should be typing exactly this:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

Do not use any of the quotes.

I just tried the first line and it worked fine. It should say "OK" after you use it.

---

### Post by bumanie on 2008-03-28
This link should help
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Also go to System --> Administration --> Sotware sources and ensure the first 4 boxes are enabled.

---

### Post by jkeyes0 on 2008-03-28
> **cisforcojo said:**
> I'm not sure about the DOCTYPE error but you should be typing exactly this:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

Do not use any of the quotes.

I just tried the first line and it worked fine. It should say "OK" after you use it.

I believe the problem the OP is having is that [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) redirects to [http://www.medibuntu.org/](http://www.medibuntu.org/), so when he does the wget to pull down the list, it's pulling down the main page of [http://www.medibuntu.org/](http://www.medibuntu.org/). If he removes the medibuntu.list he downloaded earlier and does the wget I mentioned in my last post, he should be good to go.

---

### Post by Oldsoldier2003 on 2008-03-28
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) is a official source. Follow the instructions there if you want to install the medibuntu repos.

---

### Post by c-ron on 2008-03-28
> **J.Byram said:**
> sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list"[/CENTER]

Now, when I try any sudo get-apt command in the terminal, I get this response from the terminal:
[CENTER]
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.[/CENTER]


Hi,
This happened because  [http://medibuntu.sos-sts.com/sources.list.d/feisty.list]("http://medibuntu.sos-sts.com/sources.list.d/feisty.list") is redirecting to a web page. The html for that page has been inserted into your mediabuntu.list file.
You more than likely have to manually edit the medibuntu.list file:

```
sudo nano /etc/apt/sources.list.d/medibuntu.list
```

Remove the "<!DOCTYPE ...." line.

---

### Post by Oldsoldier2003 on 2008-03-28
> **c-ron said:**
> Hi,
This happened because  [http://medibuntu.sos-sts.com/sources.list.d/feisty.list]("http://medibuntu.sos-sts.com/sources.list.d/feisty.list") is not a package. It's a web page. The html forthat page has been inserted into your mediabuntu.list file.
You more than likeley have to manually edit the medibuntu.list file:

```
sudo nano /etc/apt/sources.list.d/medibuntu.list
```

Remove the "<!DOCTYPE ...." line.

the whole page is there because of the bad url given in that tutorial...

---

