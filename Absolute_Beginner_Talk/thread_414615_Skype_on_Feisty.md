---
title: "Skype on Feisty"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-04-20
Did the repo for skype get fixed for Feisty?  There was a problem with only being able to make one call in  earlier versions of Ubuntu.  Or, do I just need to go with the deb package on the skype site?

When I go to install the deb package I get:

> A later version is available in a software channel

You are strongly advised to install the version from the software channel, since it is usually better supported.

Does anybody know if the repo is fixed?

Thanks

---

### Post by elect on 2007-04-20
Im interested too...

I cant find anythink on the repo....

---

### Post by wormser on 2007-04-20
Its there:

sudo apt-get install skype -y

I know the old repo had problems.  Hopefully somebody who knows will reply soon.

---

### Post by Obor on 2007-04-20
i'm using the debian skype repo and my skype works without problems
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

---

### Post by madmetal on 2007-04-20
my edgy system freezes for 2-3 when i had a call or event on skype..
is this problem also appear at feisty?

---

### Post by Obor on 2007-04-20
> **madmetal said:**
> my edgy system freezes for 2-3 when i had a call or event on skype..
is this problem also appear at feisty?
I had the same problem on edgy. I think its fine in feisty because i don't remember it happening yet and i'm running feisty since beta. At least on my PC it seems to be fine.

---

### Post by wormser on 2007-04-20
> **madmetal said:**
> my edgy system freezes for 2-3 when i had a call or event on skype..
is this problem also appear at feisty?

That problem is not from edgy, it is the repo for skype.  If you download the deb package from skype.com that problem will be gone.  To solve your problem,  sudo apt-get remove skype then go and download it from the site.

I prefer downloading from the repo instead of downloading the deb package.  That is why I asked my question.

---

### Post by wormser on 2007-04-20
> **Obor said:**
> I had the same problem on edgy. I think its fine in feisty because i don't remember it happening yet and i'm running feisty since beta. At least on my PC it seems to be fine.

Thanks, I will test it out and report back.

---

### Post by madmetal on 2007-04-20
> **wormser said:**
> That problem is not from edgy, it is the repo for skype.  If you download the deb package from skype.com that problem will be gone.  To solve your problem,  sudo apt-get remove skype then go and download it from the site.

I prefer downloading from the repo instead of downloading the deb package.  That is why I asked my question.

thanks! i will try it..
i also preffer repos... :popcorn:

---

### Post by weth on 2007-04-20
> **madmetal said:**
> my edgy system freezes for 2-3 when i had a call or event on skype..
is this problem also appear at feisty?

i had the same issue on Edgy, but not any longer with Feisty :)

I installed it this way:



Quote:

    sudo gksudo gedit /etc/apt/sources.list


then add at the end of the file

Quote:

    # Skype packages
    deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

... then "sudo aptitude update" and "sudo aptitude install skype" ... you'll have to accept their licence agreement and that's it :)

---

### Post by Drakkor on 2007-04-20
:)

---

### Post by wormser on 2007-04-20
> **weth said:**
> i had the same issue on Edgy, but not any longer with Feisty :)

I installed it this way:



Quote:

    sudo gksudo gedit /etc/apt/sources.list


then add at the end of the file

Quote:

    # Skype packages
    deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

... then "sudo aptitude update" and "sudo aptitude install skype" ... you'll have to accept their licence agreement and that's it :)

I just tested the feisty default repo and skype works great.  There is no need to edit /etc/apt/sources.list and add the skype repo.

---

