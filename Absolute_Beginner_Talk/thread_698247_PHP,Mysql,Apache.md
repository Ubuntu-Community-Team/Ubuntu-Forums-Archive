---
title: "PHP,Mysql,Apache"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by mmarif4u on 2008-02-16
Last night i tried to install PHP,Mysql,Apache in Ubuntu 7.10.
1st i try to check them in software list, then i open synaptic and search there.
But i did not find any thing.JUST Python was there.

What can i do now to install these.can i download from internet and then install them(LAMP). 
And from where can i open /etc/apt/source.list to uncomment these.

thanks

---

### Post by mmarif4u on 2008-02-16
Any body

---

### Post by PeterJS on 2008-02-16
You use tasksel to install the LAMP stack.
```

sudo tasksel

```

---

### Post by fatality_uk on 2008-02-16
Here's a simple point & click solution:

1) Open Synaptic Package Manager
2) From the Edit menu, click "**Mark packages by task**"
3) Click the checkbox for LAMP, ok that
4) Hit the Apply button

Ubuntu will now go off and find all the relevant parts to create a LAMP server

Hope that helps

---

### Post by mmarif4u on 2008-02-18
Thanks guys for your replies.

ubuntu will download this from internet OR will find it in repository.
Becauze i try last nite again,but fail to find it by synaptic manager.

**NOTE:i dont have internet on that PC.**
If ubuntu will download from internet,THEN how can i download a LAMP software and copy to flash drive an then install it by using terminal.
Any further help will be appreciated.

---

### Post by mmarif4u on 2008-02-18
Any idea guys...

---

### Post by hyper_ch on 2008-02-18
the downloaded packages are save in /var/cache/apt (or is it /var/apt/cache)... just copy the downloaded .deb files there and then on the other computer you can install them with

```

sudo dpkg -iGREB *.deb

```

OR

you could download the ubuntu dvd - it should have the lamp stuff on it as well as a lot of other packages.

---

