---
title: "Error...instalation Ubuntu..."
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Tom_YU on 2007-11-04
On one partition ( 10Gb) I have  installed Windows XP, on other one ( 70Gb) I planned to install Ubuntu 7.04...I started instalation and on my screen appered this messages:

_____________

hdb error code: 0X70 sense_key:0X03 asc: 0X02 ascq: 0X0

Buffer I/O error on device hdb , logical block..(some big nubmer)

____________

It was many errors like this but with difrent nubmers and other...
Does anyone knows what is this problem...?

---

### Post by overdrank on 2007-11-04
> **Tom_YU said:**
> On one partition ( 10Gb) I have  installed Windows XP, on other one ( 70Gb) I planned to install Ubuntu 7.04...I started instalation and on my screen appered this messages:

_____________

hdb error code: 0X70 sense_key:0X03 asc: 0X02 ascq: 0X0

Buffer I/O error on device hdb , logical block..(some big nubmer)

____________

It was many errors like this but with difrent nubmers and other...
Does anyone knows what is this problem...?

Hi, you may what to check the disc for erorrs.  this link I think may help 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 
Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Tom_YU on 2007-11-05
overdrank this first link is for burning image filo to cd...I don' need that,I have wright cd Ubuntu 7.04...
And this second link I don't understand...But thanks anyway!
It's maybe problem in combo box ( cd writer,dvd reader all in one)...my cd-rom is good at reading DVD ,but very bad at reading CD...I am gonna buy a new DVD writer in a few days and I think maybe solve this problem...

---

### Post by 3rdalbum on 2007-11-05
When you say that you started installation, do you mean that:

You booted up the live CD
It booted to the desktop
You double-clicked on the Install icon
You followed the prompts until it gave you a progress bar which said "Installing..."?

If so, and that's the point where you got the errors, then "hdb" is likely to be the hard disk that you are installing to, and the errors are probably reporting disk damage.

If, on the other hand, the Ubuntu Live CD is simply **booting** (black screen with Ubuntu on it and a progress bar, and then you get white text on a black background reporting these errors), then you will want to burn your copy of the CD at a slower speed, like 8x. And use good quality CD media.

---

### Post by Tom_YU on 2007-11-05
3rdalbum

It's like this :

"If, on the other hand, the Ubuntu Live CD is simply booting (black screen with Ubuntu on it and a progress bar, and then you get white text on a black background reporting these errors), then you will want to burn your copy of the CD at a slower speed, like 8x. And use good quality CD media."

I will do that and try it again.
Thanks!

---

