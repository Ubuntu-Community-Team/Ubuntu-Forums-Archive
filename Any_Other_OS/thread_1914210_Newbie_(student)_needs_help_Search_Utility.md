---
title: "Newbie (student) needs help: Search Utility"
date: 2012-01-23
forum: Any Other OS
---

### Post by Madyimages on 2012-01-23
Good Evening Guys,

Im a total newbie on Ubuntu, I use a linux Mint 11. Im going to a local college for winter season, and apparently theres no campus available on the course so i bravely took the online class. My main problem is that its kinda hard to reach my instructor, if i got a question i send him email in the morning and i get the reply at night. Also the regular 15 week course in compress to 4 weeks. So i find it the hard way that its hectic. sigh. anyway my question is, how do i open a file that he sent on email to my terminal? cause we have an assignment and i can't just open the file on terminal... and this is just the icing of the assignment. im ready to quit. any input is appreciated

---

### Post by pr3zident on 2012-01-23
> **Madyimages said:**
> Good Evening Guys,

Im a total newbie on Ubuntu, I use a linux Mint 11. Im going to a local college for winter season, and apparently theres no campus available on the course so i bravely took the online class. My main problem is that its kinda hard to reach my instructor, if i got a question i send him email in the morning and i get the reply at night. Also the regular 15 week course in compress to 4 weeks. So i find it the hard way that its hectic. sigh. anyway my question is, how do i open a file that he sent on email to my terminal? cause we have an assignment and i can't just open the file on terminal... and this is just the icing of the assignment. im ready to quit. any input is appreciated

what type of file is it ? and what are you trying to do with this file ?

---

### Post by SuaSwe on 2012-01-23
Hi Madyimages,

What kind of file is it? Identify what directory the file is located, navigate to it (cd /path/to/dir) and type 'file <filename>'; what kind of file is listed?

---

### Post by Madyimages on 2012-01-23
[https://ccbcmd-bb.blackboard.com/bbcswebdav/pid-1410031-dt-content-rid-5226969_1/courses/DCOM142.10607.201211/us-colleges.txt](https://ccbcmd-bb.blackboard.com/bbcswebdav/pid-1410031-dt-content-rid-5226969_1/courses/DCOM142.10607.201211/us-colleges.txt)

a txt file i think

---

### Post by SuaSwe on 2012-01-23
Looks like it. :) Have you downloaded it to your computer? Do you know where it's located? If you have downloaded it but don't know where it's located, go to Terminal and do:

```

find ~ -type f -name us-colleges.txt

```

That should give its location, for example:

/home/user/us-colleges.txt

You can then "cat" the file to read it, or if you prefer to scroll through it page by page, use "less", e.g.:

```

cat /home/user/us-colleges.txt     <=== will show the whole file
less /home/user/us-colleges.txt     <=== will show the file page by page

```

Does that help? Note that if you've not downloaded the file to the hard drive yet, you won't find it. 

Why is it that you need to view it in Terminal, by the way? Is that part of the task or are you not familiar with any GUI text editors on Mint?

---

### Post by Madyimages on 2012-01-23
^^ you got it. its part of the activity that were doing, and i cant make a progress to the project. but you got me going this time. thanks alot

---

### Post by SuaSwe on 2012-01-24
No probs, let us know if you need further help! The thread can be marked as solved using Thread Tools once you're all set. :)

---

