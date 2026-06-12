---
title: "RPM file installation"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by pisapiag on 2006-10-01
I've been using Windows for the last 20 years. I'm tired of paying money to the richest guy in the world. I checked myself into rehab so I installed Dapper Drake on an old PC (Asus P3B-F). I'm actually amazed at how easy it was. I want to install Limewire. I downloaded the Limewirelinux.rpm file and now I'm stuck. ](*,)  I found out I need to install Alien in order to be able to read and install the package. Alien is now installed. Now what? :confused:  
Please, I'm a total newbie with Linux and console commands and what not. If you post an answer, please be as detailed as possible as if I were a seven year old. From what I understand so far, installing software is not Linux's forte.
Thanks.

---

### Post by unisol on 2006-10-01
sudo aptitude install alien
sudo alien -i LimeWire*.rpm

---

### Post by Sef on 2006-10-01
Here's a link that you should read [How to install anything]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by pisapiag on 2006-10-01
Thank you all. I did all that you instructed me to do. Now, I can see Limewire in the Applications group under Internet but when I click on it, nothing happens:???: . Is there something I should do to make it work?
Thanks.

---

### Post by sumguy231 on 2006-10-01
Limewire requires Java, make sure you have that.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
After that, you may need to
```
sudo update-alternatives --config java
```
If it still fails, run it from a terminal and paste the output.

---

### Post by mips on 2006-10-01
**sudo apt-get install frostwire** or via synaptic

[http://www.frostwire.com/](http://www.frostwire.com/)

Frostwire is the same thing as limewire, it's just truly free which limewire is not. 

Keep in mind you need Java first in order to run frostwire/limewire.

You could also use Automatix to install frostwire which is the *free* version of limewire.

Maybe look at GTK Gnutella which is in the repositories and will download Limewire stuff as well.

[http://gtk-gnutella.sourceforge.net/en/?page=features](http://gtk-gnutella.sourceforge.net/en/?page=features)

---

### Post by pisapiag on 2006-10-01
OK mips!
I believe I goofed. I told you I was a total newbie. I pasted your HTTP link as a new channel. Now, the updates won't work. It tells me I should edit the etc/apt/sources.list file to remove the added line. But when I try to do that, the system tells me that I am not the owner of that element and that I can't change the permissions. I am logged in as the administrator. What should I do?

---

### Post by mips on 2006-10-01
> **pisapiag said:**
> OK mips!
...I pasted your HTTP link as a new channel. ...

What do you mean by the above, I don't understand ?

You can edit your sources list with:
```
sudo gedit /etc/apt/sources.list
```

But before you carry on tell me what you did ?

---

### Post by pisapiag on 2006-10-01
Thanks MIPS;
I use Ubuntu in French as I am French a speaking fellow living in Quebec. I use the English forums as I believe they are more diligent in answering, mostly because there are more of expert users willing to contribute and help us than the French ones.
There is an application called "Gestionnaire de canaux logiciels" which could tranlate into "Software channels manager" under Système -> Administration. That's where you could manually add "channels" like deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free.
I thought you link could be used as a channel to get the Limewire app.
Your command code worked. I ran it and I could then edit and save the sources.list file. But after having run the code supplied by sumguy231, Limewire still won't launch although it seems available in Applications->Internet. 
What should I do next?

---

### Post by mips on 2006-10-01
First: Have you installed Sun Jave ?

Two: If you open Synaptic type in  Frostwire and it should find it. You might have to enable the multiverse or universe repositories and update first.

The link I posted was just for information sake.

You might want to look at Automatix, just google the name but it is better to install stuff yourself as you learn things.

---

### Post by pisapiag on 2006-10-01
MIPS
Synaptic shows java-common and java-gcj-compat as installed. Limewire-free is listed as installed (local or obsolete). Frostwire does not show up.

---

### Post by pisapiag on 2006-10-02
I got fed up with trying to make Limewire work. :evil:  So I went and downloaded the Ubuntu/Debian specific Frostwire software. The installation seemed to have gone smoothly with no hitch whatsoever. :)  Then I go in the Applications menu under Internet and there it is. Great! Now I click on the Frostwire icon and... nothing happens. ](*,) 
What gives??? Help please.

---

### Post by mips on 2006-10-03
Do you recall install Sun Java ?

I suspect you did not. [https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e](https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e)

Limewire/Frostwire needs java to work.

Could I suggest you maybe look at Automatix.

---

