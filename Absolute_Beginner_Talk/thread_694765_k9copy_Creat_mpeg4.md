---
title: "k9copy Creat mpeg4"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-02-12
Hello!
I wanted to make a mpeg4 from my dvd. The process went to 100%, but nothing happened and it was in 100 for minutes. I cancelled it, and the file which made by k9copy was only sound and no picture!
What can I do?
Thanks.

---

### Post by PriceChild on 2008-02-12
When at 100%, it was probably just doing the final touches, counting something or other for the container. Next time don't be hasty to cancel.

If you have it available, please paste the log here.

---

### Post by Hoom@n on 2008-02-12
Thanks, but do you think it's better to: "sudo apt-get install dvdrip"? (Please tell me what is better by installing dvdrip)

---

### Post by PriceChild on 2008-02-12
I have no experience.

---

### Post by FuturePilot on 2008-02-12
You may need libdvdcss from the Medibuntu repos.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install libdvdcss2
```

---

### Post by mc4man on 2008-02-13
In terms of a 1 click app to do the conversion you wanted k9's not bad, certainly not the greatest. For some reason mencoder can silently crash, leaving k9 running (basically doing nothing). And for some other unknown reason this usually just happens once - then it works fine. So if you want to see how k9 does try it again. You can check that all is well with system monitor - while encoding there should be both a k9copy and mencoder process

---

### Post by Hoom@n on 2008-02-14
Thank you, I'll try them later.

---

### Post by ajclarkson on 2008-02-14
i had this exact same problem last night, and i have to say that after a lot of stress I discovered that it was mencoder which had crashed, since then I have used the program 3 times absolutely perfectly, bit of a strange problem this one.....

---

### Post by Hoom@n on 2008-02-16
You mean there is no way to solve it?

---

### Post by bumanie on 2008-02-16
Personally, I would use k9copy to make the dvd into a dvd5 and then put the output of that into the program devede to make it into an avi. Alternatively, dvdrip will do this with one click, but I found the program very slow, although the output was good. I admit I have minimal experience with k9copy so won't comment, but have found devede very good overall. One thing to watch out for is a coding problem with the sound. As you are using gutsy, as long as you have backports enabled, this should be fixed. Get devede from here if you are interested [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)
Take not of the 'note to gutsy users' near the top of the page

---

