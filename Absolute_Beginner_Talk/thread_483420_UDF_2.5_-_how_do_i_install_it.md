---
title: "UDF 2.5 - how do i install it?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2007-06-24
Tried following the instructions on this thread, but just dont understand it...

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)


Where exactly is the file:
> A UDF 2.5 filesystem driver (the UDF driver included in Feisty Fawn 7.04 only supports UDF 2.0). A driver for Feisty Fawn's 2.6.20-15 kernel is attached to this page. Copy it to /lib/modules/2.6.20-15-generic/kernel/fs/udf/udf.ko 


The only thing close to an attachment is the link to a patch file in the further reading section.

>  Linux UDF project containing UDF-2.50_linux-2.6.20.patch, the UDF 2.5 filesystem driver. 


That is even more cryptic as it gives no instructions or basic requirements to run the .patch file.



Can anyone give me some simplistic instructions to add supposrt for UDF 2.5 to my linux box?


FYI its running 7.04, 2.6.20-16-generic.


Tnx.

---

### Post by Scorpuk on 2007-06-25
Anyone?

---

### Post by Scorpuk on 2007-06-28
nobody? :(

---

### Post by keyboardslave on 2007-08-26
im in the same boat mate... its weird how that one site mentions its attached..

---

### Post by schorsch on 2007-08-26
The patch and installation instructions are available right [here]("http://sourceforge.net/tracker/index.php?func=detail&aid=1476807&group_id=295&atid=300295").

---

### Post by pwn on 2007-12-26
So did anybody get it working? There are no instructions for Gutsy

---

### Post by maethor on 2008-04-05
> **pwn said:**
> So did anybody get it working? There are no instructions for Gutsy

I got it working. It involved compiling a patched kernel and copying the resultant udf.ko to the correct location. I used the alternative build method described here: [https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod](https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod)

---

### Post by Hikash on 2008-04-08
Hey,

So, I'm following the alternate method guide, and I'm at the point where you need to make either the xconfig or menuconfig, but I'm not sure which to choose.

Furthermore, I'm not sure how to apply the patch here. I'm pretty new to linux and although I know how to navigate around the command line for the most part, but I'm not sure how to apply patches and so forth. 

Any additional steps you could provide would be much appreciated.

---

