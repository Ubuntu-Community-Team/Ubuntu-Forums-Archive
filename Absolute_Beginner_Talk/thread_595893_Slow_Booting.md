---
title: "Slow Booting"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by jd3010 on 2007-10-29
I have an older PC and would like to know if there are any services I can terminate (how do I do that ??) to make the booting and generally the PC faster.

I installed already preload (but cannot see where I can configure it ??)

thanks

---

### Post by erginemr on 2007-10-29
Unfortunately, you do not have much choices becasue Ubuntu is kind of optimized already. You should disable Compiz which really has a big impact on the performance. 

And there is a file in /etc folder, "/etc/host" which starts with the following two lines:
127.0.0.1       localhost 
127.0.1.1       your_computer_name

You may try changing the first line into:
127.0.0.1       localhost your_computer_name
127.0.1.1       your_computer_name

where your_computer_name is listed on the second line. Some people say this will make your system a bit faster.

Other than that, I can suggest you to use Xubuntu instead.Xubuntu uses Xfce desktop and performs much better on older systems. Besides, it is also based on GTK+ as in Gnome. So, the overall look is the same and what's more, you can install all programs that you like in Ubuntu to Xubuntu as well.

---

### Post by jd3010 on 2007-10-29
> **erginemr said:**
> Unfortunately, you do not have much choices becasue Ubuntu is kind of optimized already. You should disable Compiz which really has a big impact on the performance. 

And there is a file in /etc folder, "/etc/host" which starts with the following two lines:
127.0.0.1       localhost 
127.0.1.1       your_computer_name

You may try changing the first line into:
127.0.0.1       localhost your_computer_name
127.0.1.1       your_computer_name

where your_computer_name is listed on the second line. Some people say this will make your system a bit faster.

Other than that, I can suggest you to use Xubuntu instead.Xubuntu uses Xfce desktop and performs much better on older systems. Besides, it is also based on GTK+ as in Gnome. So, the overall look is the same and what's more, you can install all programs that you like in Ubuntu to Xubuntu as well.
Thnaks a lot...

I also saw that IP6 is enabled ... is there a way to disable it ?

As I did a complete install of Ubuntu 7.10, I saw that there are a lot of programms running and installed .... Is there any I can get rid of immediately ?

Thanks again

---

