---
title: "Maverick Themes on Lucid"
date: 2010-10-13
forum: Art &amp; Design
---

### Post by teejay17 on 2010-10-13
This may have been covered already, but if it has, I can't for the life of me find the information anywhere. In a nutshell, I would like to know how to install the Maverick themes on Lucid. 
Thanks in advance.

---

### Post by teejay17 on 2010-10-14
Is it simply a matter of using the command line to install the themes?

---

### Post by TBABill on 2010-10-16
I'm wanting to do the same thing and have been unable to find out how to do it. Anyone?

---

### Post by exploder on 2010-10-16
Here is what you are after. :)

[http://www.techdrivein.com/2010/08/how-to-install-updated-light-themes-for.html](http://www.techdrivein.com/2010/08/how-to-install-updated-light-themes-for.html)

---

### Post by NightwishFan on 2010-10-16
Just install this ppa using these commands.

```
sudo add-apt-repository ppa:murrine-daily/ppa
```
Then:
```
sudo apt-get update
```
Finally:
```
sudo apt-get install light-themes gtk2-engines-murrine
```

Enjoy. I have tested this and it works.

---

### Post by TBABill on 2010-10-16
Hmmmmm....all the terminal codes worked fine but I still don't see the choice of the ubuntu font in the repo. Am I missing something?

---

### Post by NightwishFan on 2010-10-16
Font is a different matter, just open the source package and install the regular font. There is also a thread about this in the community cafe.

[https://launchpad.net/ubuntu/maverick/+source/ubuntu-font-family-sources](https://launchpad.net/ubuntu/maverick/+source/ubuntu-font-family-sources)

---

### Post by exploder on 2010-10-16
Instructions are here.

[http://www.webupd8.org/2010/10/public-ubuntu-font-family-ppa-for.html](http://www.webupd8.org/2010/10/public-ubuntu-font-family-ppa-for.html)

---

### Post by TBABill on 2010-10-16
Thank you. Exploder's link worked perfectly. Much appreciated everyone! Desktop looks better already.

---

