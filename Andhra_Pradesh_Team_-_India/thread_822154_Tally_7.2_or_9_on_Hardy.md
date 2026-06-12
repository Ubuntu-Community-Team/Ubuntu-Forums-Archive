---
title: "Tally 7.2 or 9 on Hardy"
date: 2008-06-07
forum: Andhra Pradesh Team - India
---

### Post by be4truth on 2008-06-07
Hi Everybody,

I am still struggling with Tally on Hardy. This is one of the main blocker in office migration. Any help is appreciated.

---

### Post by abhiomkar on 2008-06-10
Hi There,

I have tried installing Tally in Hardy with **wine**. It was running flawlessly in Hardy. I Installed it and it is running.

Download install.exe from here to Home folder: [http://www.tally.co.in/download9.shtml](http://www.tally.co.in/download9.shtml)

Open Terminal, then enter these commands.

```
sudo apt-get install wine
```

Install the tally

```
wine install.exe
```

Then, run the tally with wine

```
wine ~/.wine/drive_c/Tally/tally9.exe
```

But, i am not sure whether the tally is fully functionable in Linux.

> **be4truth said:**
> Hi Everybody,

I am still struggling with Tally on Hardy. This is one of the main blocker in office migration. Any help is appreciated.

---

### Post by be4truth on 2008-06-10
Did somebody activate Tally under wine and is using it? I know that Tally 9 installs but as far as I know it doesn't activate under Hardy. Does anybody have an experience?

---

### Post by fourthofjuly on 2008-08-21
> **be4truth said:**
> Did somebody activate Tally under wine and is using it? I know that Tally 9 installs but as far as I know it doesn't activate under Hardy. Does anybody have an experience?
works in educational mode only...

when i enter serial number, key & e-mail id - error reads              

"COULD NOT ACTIVATE
INSUFFICIENT PERMISSIONS"

any suggestions please?

---

### Post by mosaic2s on 2008-08-21
try virtualbox for such situations.

---

### Post by be4truth on 2008-08-21
Why using VirtualBox on Hardy if this machine is for bookkeeping only? Then the machine can stay on Windows.

---

### Post by fourthofjuly on 2008-08-24
anyone, please?

thanks, any help will be appreciated...

regards,

devang.

---

### Post by be4truth on 2008-08-24
> **fourthofjuly said:**
> anyone, please?

thanks, any help will be appreciated...

regards,

devang.

Cracked versions don't try to activate. They work. But use them only when you have a license:lolflag:

---

### Post by fourthofjuly on 2008-08-25
> **be4truth said:**
> Cracked versions don't try to activate. They work. But use them only when you have a license:lolflag:
had I been using cracked versions, there was no question of Tally prompting for any serial no. and key?

I am using LICENSED Tally... without a doubt...

did you mean cracked version will work? pl clarify

---

### Post by aiser on 2009-12-01
:ks

---

### Post by bikusuma on 2010-01-07
We had this problems too

We use Tally 7.2 Release 3.14. If i modify the tally.ini file and directing Tallylicenseserver to the tally server it will create error message like this:
Error!
Software Exception c0000005
(Memory Access Violation)

If no modification in the tally.ini file it will always asking the serial number even if we enter correctly (we purchase the licensed one) and the status still EDUCATIONAL.

Try to ask tally customer care and you will have answer: sorry we don't support open source...

any help, please..

---

### Post by aneeshk_k on 2010-01-14
Same issue for me also- Unable to activate Tally using wine. 
As Tally 7.2 supports only Redhat Linux, I tried installing that on CentOS and it worked just fine. Only issue is that the printing option is not working. Using Wine, printing does works but I had to activate Tally every time I open it :(

---

