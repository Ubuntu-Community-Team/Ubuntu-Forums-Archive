---
title: "Frostwire+java?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-13
i get a messege when im typeing in frostwire in terminal ...


Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


How do i upgrade to JRE 1.4.x or newer?

---

### Post by RobsterUK on 2006-09-13
I also had this problem.

Check you have java installed in Applications > Add/Remove

If it still doesn't work read my post here for how to edit runFrost.sh to fix it
[http://www.ubuntuforums.org/showthread.php?t=255275&page=2](http://www.ubuntuforums.org/showthread.php?t=255275&page=2)

---

### Post by haxer on 2006-09-13
Any easier way? pleade im a total newbie to linux

---

### Post by Kilz on 2006-09-13
> **haxer said:**
> Any easier way? pleade im a total newbie to linux

Thats the equivalant of asking a windows user to see if the program is in add/remove programs in controll panel and if not read this page about a patch. There is no easier way.

---

### Post by haxer on 2006-09-13
Ok i couldnt find it on that list but when i go to system then options or something dont know the word in english its the top option of that little list that come up then i see sun java-control panel and sun-java policy tool how is that possible and how do i solve this little problem im havin?

---

### Post by IusedTObeSOMEONEelse on 2006-09-13
today I had to re-install every thing after a serious crash. I enable supported and non supported in add/remove  and i was able to get java 1.4 & sun java 5.0 installed. Try that. It worked for me. Good Luck!!

---

### Post by haxer on 2006-09-13
Where do i find that option?

---

### Post by skymt on 2006-09-13
> **haxer said:**
> Where do i find that option?

Didn't I fix your Frostwire problem in [your Azureus thread](http://www.ubuntuforums.org/showthread.php?t=256826)? You should have the right Java set up now.

---

### Post by haxer on 2006-09-13
Yeah i did but wanted to try hes option to all i perfectly running but i would like to know how he did that maybe i can find different things there i really thank you for your answer and it was really nice but i also wants to look up other options to :) so please dont be hateing :P

---

### Post by skymt on 2006-09-13
Not hating, making sure your problem was solved! I didn't know whether you had tried Frostwire since running update-alternatives.

Anyway, assuming the option you're talking about is MustangSallydd's mention of enabling supported and non-supported in add/remove, here's how (assuming you haven't changed certain things):

* Go to System > Administration > Software Properties
* In the list, select "Ubuntu 6.06 LTS (Binary)"
* Click Edit
* Make sure all four checkboxes are checked

---

