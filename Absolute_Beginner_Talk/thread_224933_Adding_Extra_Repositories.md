---
title: "Adding Extra Repositories"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-07-28
Hi
I'm trying to add some FF plug-ins but find that they are not available for installation.
So, to make them available, I have tried to "activate" the Universe and Multiverse repositories.
To do this I go System->Administration->Software Properties, then Add and then check the Universe and Multiverse boxes.
Then I click Add again, Close and Reload. 
However, immediately afterwards, when I look in the Software Properties dialog box, the Universe and Multiverse boxes are once more unchecked.
Can somebody please tell me if I'm forgetting something?

Thanks
Paul

---

### Post by Jagot on 2006-07-28
Try this method:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by PaulFXH on 2006-07-29
Hi Jagot
Thanks for your reply.
I went ahead with what you suggested.
However, when I try to "activate" the Universe and Multiverse repositories, they are ALWAYS unchecked.

Indeed, immediately after going through the procedure you suggested, which finished without problems, I found that these two repositories in System->Administration->Software Properties are STILL unchecked.

Nevertheless, later on I had to install something called flashplugin-nonfree in Synaptic. Does the fact that this package was available for installation (and installed without problems) imply that the Multiverse repository is in fact available to me, despite it not being checked in the box referred to above?

I'm puzzled

Paul

---

### Post by s_h_a_d_o_w_s on 2006-07-29
do that unchecking, close, then 


sudo apt-get update

---

### Post by PaulFXH on 2006-07-29
Hi s_h_a_d_o_w_s  

OK, I did what you suggested with the Universe and Multiverse repositories EITHER both unchecked or both checked and ran the command you suggested.
However, each time, these two repositories remained UNCHECKED when I open the System->Administration->Software Properties box and click Add.

I am unclear as to whether or not they SHOULD remain checked.

Can anybody please clarify?

Thanks
Paul

---

### Post by confused57 on 2006-07-29
You can check your sources.list:

```
cat /etc/apt/sources.list
```

if there isn't a # in front of the repository, they're enabled.

To add repositories:
```
sudo gedit /etc/apt/sources.list
```

I noticed the same thing you did when enabling extra repositories using SPM.

---

### Post by PaulFXH on 2006-07-29
Hi confused57

OK, thanks for that very helpful reply.
When I checked in sources.lst, only what were obviously comments were commented out indicating that I do indeed have ALL of the repositories enabled.
How strange that they remain unchecked in the Software Properties box even after being enabled.

Thanks again for clarifying this mystery for me
Paul

---

