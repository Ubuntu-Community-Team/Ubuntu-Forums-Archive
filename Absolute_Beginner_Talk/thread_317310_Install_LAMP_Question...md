---
title: "Install LAMP Question.."
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by dmtrs on 2006-12-12
Hello everyone, i'm using UBUNTU 6.10 and i wonder if i can install LAMP. Is there any way? Should i unistall it and install other version?

Thank you. (Sorry for my poor english)

---

### Post by hyper_ch on 2006-12-12
You may want to have a look at that:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

---

### Post by dmtrs on 2006-12-12
thank you for the link. so i have to install the server edition and follow the instructions. 
...but is there any way to install L(**AMP**) as a package or something?

thanks again

---

### Post by hyper_ch on 2006-12-12
No no, this setup is for a pure server :)
So you can skip the first couple of pages and start with page 3:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p3)

Even a few things can be skipped there:
3 Enable The root Account --> not necessary I think
4 Install The SSH Server --> I would make that, so that you can login to your computer from anywhere... (but not necessarily required)
5 Configure The Network --> I guess you have your network already configured.. :) so no need to worry about that
6 Edit /etc/apt/sources.list And Update Your Linux Installation --> I would enable all repos in there :)
7 Change The Default Shell --> Do that :)

And on page 4 you then actually start the whole install thing:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4)

You have to see if you need all of that... the quote and postfix stuff you may not need... this setup is a full guide on how to prepare a server for webhosting :) There's also different sections about php, mysql, apache... maybe you just need that :) Have a look at it :)

---

### Post by dmtrs on 2006-12-12
thank you for your posts. i'will try it. :) :)

---

### Post by hyper_ch on 2006-12-12
well, if you start doing all there from page 3 then in the end you could also add ISPConfig which is a free control panel as server admin to manage the different websites incl. email and stuff...
However if you just locally want develop some stuff the bits and pieces about mysq, php, apache are fine there :)

It's up to you... you have the choice :)

---

