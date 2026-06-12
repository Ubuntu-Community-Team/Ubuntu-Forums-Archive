---
title: "Small Question About Graphics Card"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-01-26
Hello, I am now hopefully going to install Ubuntu on my main desktop machine. I have one question though.

I have a ATI RADEON X600 256MB HyperMemory graphics card in there. Will I need any drivers for Ubuntu? If so, how can I install them?

Thanks for your time.

---

### Post by luisromangz on 2008-01-26
You will need to use the propetary ATI drivers if you want 3D acceleration, and to use desktop effects and that kind of stuff.

You should be able to install them from the Restricted Drivers Manager (which will popup the first time you run Ubuntu) provided you have a working internet connection. You can also, and this is what I actually advice, download a newer version of that drivers from ATI drivers webpage. The newer drivers are faster and have fewer bugs and more features, for example, they allow you to use Compiz without using XGL.

---

### Post by CheShA on 2008-01-26
Ubuntu should support your card OK and should install stable drivers for it automatically.  If its usiing a Restricted (non free) driver, the restricted driver manager will pop up on first boot and let you know.   If you wish to use the latest drivers, by far the easiest way is to install a program called "envy" available as an Ubuntu package from albertomilone.com.  This will provide you with a gui to get, compile and install the latest drivers for your card.

---

### Post by Kilz on 2008-01-26
> **Crumpets and Jam said:**
> Hello, I am now hopefully going to install Ubuntu on my main desktop machine. I have one question though.

I have a ATI RADEON X600 256MB HyperMemory graphics card in there. Will I need any drivers for Ubuntu? If so, how can I install them?

Thanks for your time.

If you want to install the proprietary ati video drivers [you can follow this howto]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"). They will give the best acceleration. But they are not always needed.

---

### Post by Crumpets and Jam on 2008-01-27
Could I not just go to ATi's website, select my graphics card and download there installation package for Linux?

---

### Post by shad0w_walker on 2008-01-27
Trust the forum on this. Use the restricted driver manager or one of the tutorials. Unless you know precisely what you are doing the package from the website is a nightmare.

---

