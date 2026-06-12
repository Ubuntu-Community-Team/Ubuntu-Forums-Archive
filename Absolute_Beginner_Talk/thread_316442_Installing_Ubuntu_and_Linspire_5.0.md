---
title: "Installing Ubuntu and Linspire 5.0"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by soonercntry on 2006-12-10
Hey there linux lovers:

I'm looking to install both Ubuntu and Linspire 5.0.   I currently have XP Pro on one of my partitions.  I have another hard drive that I installed and formatted today (100 GB) that I would like to install Ubuntu and Linspire on.  

Ubuntu's installation looks like it could possibly be easier if I use instlux.  Should I do this?  I'm going to need to be walked through all of this.

Also, what size partitions should I create for Ubuntu and Linspire?  I'm assuming that I will create partitions just large enough for both OS's and then create another one for data storage.  

Should I install Ubuntu or Linspire first, or does it matter?

---

### Post by igknighted on 2006-12-10
For your second disc I would do this:
part 1) 1 GB linux swap
part 2) 20 GB ext3 for Ubuntu
part 3) 20 GB ext3 for linspire
part 4) 59 GB shared /home partition

I would simply use the standard Ubuntu install CD, set the partitions as shown above via the custom partitioning option, then mount them in the appropriate locations (swap for part 1, / for part 2, /linspire for part 3 and /home for part 4).

Then, install linspire, making sure to mount the partitions properly (swap for part 1, /ubuntu for part 2, / for part 3, and /home for part 4).  If you make both use the same username, then they will share a folder in /home, which has benefits and drawbacks, I would probably make different usernames, but that's just me.

---

### Post by soonercntry on 2006-12-10
That's exactly what I was looking for.  Thanks so much.  Quick question again.  Why so much space for Ubuntu and Linspire?  Do I need that space for complimentary programs to be installed in the future?

---

### Post by igknighted on 2006-12-10
I always leave a lot of space, you could definitely go with less though.  I just like to leave enough room for anything I could ever want to install.  10 or 15 GB would certainly do though.

---

### Post by soonercntry on 2006-12-11
I'm typing this from firefox in my newly installed Ubuntu 6.1 OS!!!!!!

Feels good to think that my dependency on M$ just took a huge leap in the non-dependent direction!

---

