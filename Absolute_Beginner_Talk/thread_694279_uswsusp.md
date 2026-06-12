---
title: "uswsusp"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by phoenix5002 on 2008-02-11
I'm trying to fix my laptops suspend and hibernate features.  It will successfully suspend or hibernate but there is a black screen upon resume.

Anyway I see that it is recommended to use uswsusp to fix this problem however I tried this before "sudo apt-get install uswsusp" and I got a blue screen in the terminal saying it hadn't detected a swap partition should I let uswsusp define one or something like that...
Well I decided I wanted to cancel the operation at this point because that didn't sound good to me so I selected no and then pressed ctrl+c to stop it.  Then the next time I turned on my laptop I got a kernel panic message and I ended up reinstalling ubuntu to fix it.

ok...so now I'm just wondering, becaue I'm more than likely going to run into that same prompt this time around, should I select yes or no?  Also, is that normal?  is there something I should do first?

---

### Post by louieb on 2008-02-11
In order to hibernate you need a swap partition. That where the resume image is stored. Haven't used uswsusp so can't comment on it.

Just wondering do you have a swap partition? Unless you used manual partitioning one should have been created during the install.

And if you do is it being used? You can use the resource tab in System>Administration>System Monitor. or the** top **command.

If you find you don't have a swap partition I guess using uswsusp is a good a  way as any to get one. 
 I

---

### Post by phoenix5002 on 2008-02-12
Yes I have 1.3GB of swap, and 0bytes are being used.

---

