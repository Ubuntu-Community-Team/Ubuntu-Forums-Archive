---
title: "iSight green capture issue"
date: 2009-04-21
forum: Apple Hardware Users
---

### Post by Claritux on 2009-04-21
I'm having the green capture issue in iSight as described in the MacBook4-1/Jaunty guide
[https://help.ubuntu.com/community/MacBook4-1/Jaunty#iSight](https://help.ubuntu.com/community/MacBook4-1/Jaunty#iSight)

I've tried to add
```
v4l2src device="/dev/video0" ! videoscale
```
to gstreamer-properties. It works, but when I try to exit gstreamer-properties it won't save the changes.

Anybody got a solution?

[http://dl.getdropbox.com/u/955480/Green_capture_issue_example.jpg](http://dl.getdropbox.com/u/955480/Green_capture_issue_example.jpg)

Update:
I've tried to edit the value in gconf-editor by going to system->gstreamer->0.10->default and put the value into videosrc, but it seems like the value for some reason resets every time I open a video-capturing app. like Cheese.

---

### Post by Claritux on 2009-04-23
*Bump*

I'd really like to be able to use Cheese properly on my MacBook.
The problem doesn't occur in aMSN for some reason.

---

### Post by jaos on 2009-04-23
> **akshov said:**
> I'm having the green capture issue in iSight as described in the MacBook4-1/Jaunty guide
[https://help.ubuntu.com/community/MacBook4-1/Jaunty#iSight](https://help.ubuntu.com/community/MacBook4-1/Jaunty#iSight)

I've tried to add
```
v4l2src device="/dev/video0" ! videoscale
```
to gstreamer-properties. It works, but when I try to exit gstreamer-properties it won't save the changes.

Anybody got a solution?

[http://dl.getdropbox.com/u/955480/Green_capture_issue_example.jpg](http://dl.getdropbox.com/u/955480/Green_capture_issue_example.jpg)

I have the same problem with 3.1 macbook.

---

### Post by cyberdork33 on 2009-04-23
sounds like a problem with gstreamer. can you try ekiga? it should work there.

---

### Post by Claritux on 2009-04-23
I just tested in Ekiga and Skype. Same problem occurs :/

---

### Post by elamericano on 2009-04-24
For me it is saving in videosrc, but cheese has its own entry for webcam device in gconf. I can't make it work no matter what gets saved.

---

### Post by mabovo on 2009-04-24
> **jaos said:**
> I have the same problem with 3.1 macbook.

Same for 2.1 MacBook.

---

### Post by GF_Sobriquet on 2009-04-25
> **mabovo said:**
> Same for 2.1 MacBook.

I have the same problem with MacBook Pro 1,1

---

### Post by Bl@de on 2009-04-25
Same problem here with my macbook 1,1 on latest 9.04.
It was working correctly on Intrepid :(

---

### Post by cyberdork33 on 2009-04-25
I think this is a bug in Jaunty against gstreamer. I haven't had time to test things yet myself, but if someone else would like to file a bug in launchpad....

---

### Post by Claritux on 2009-04-27
Bug report: [https://bugs.launchpad.net/ubuntu/+bug/349255](https://bugs.launchpad.net/ubuntu/+bug/349255)

---

### Post by nTia89 on 2009-05-15
same problem with my macbook 2,1

---

### Post by mabovo on 2009-05-15
> **nTia89 said:**
> same problem with my macbook 2,1

I've applied the patch in Launchpad and green issue has gone.

Mac2,1 - Jaunty(Kernel 2.6.30-RC5).

---

### Post by tiagobt on 2009-05-16
Yes, the patch solves the issue in Cheese, but Skype and aMSN are still affected by the green capture issue.

---

### Post by NoBugs! on 2009-06-07
> **tiagobt said:**
> Yes, the patch solves the issue in Cheese, but Skype and aMSN are still affected by the green capture issue.

The bottom of [this page]("https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/345080") describes a more system-wide fix, using the previous Intrepid driver version. However, the system-updater keeps wanting to change it back.

---

### Post by volanin on 2009-06-07
Thank you!
To avoid the system-updater annoyance, just:

```
$ sudo aptitude hold lib32v4l-0 libv4l-0
$ echo "lib32v4l-0 hold" | sudo dpkg --set-selections
$ echo "libv4l-0 hold" | sudo dpkg --set-selections

```

---

### Post by robin.nightingale on 2009-06-07
Could anyone help me with Patching ?

When i: Type patch -p0 < isight.diff
i get the following error:

mogli@xxy:~/Desktop$ patch --po < isight.diffcan't find file to patch at input line 4
Perhaps you should have used the -p or --strip option?
The text leading up to this was:
--------------------------
|diff -ur cheese-2.26.0.orig/src/cheese-webcam.c cheese-2.26.0/src/cheese-webcam.c
|--- cheese-2.26.0.orig/src/cheese-webcam.c 2009-03-16 18:46:10.000000000 +0100
|+++ cheese-2.26.0/src/cheese-webcam.c 2009-05-11 18:35:45.960992276 +0200
--------------------------
File to patch:

What do i wrong.
P.S. i have totaly no experience with patches.

---

### Post by cyberdork33 on 2009-06-07
> **robin.nightingale said:**
> Could anyone help me with Patching ?

When i: Type patch -p0 < isight.diff
i get the following error:

mogli@xxy:~/Desktop$ patch --po < isight.diffcan't find file to patch at input line 4
Perhaps you should have used the -p or --strip option?
The text leading up to this was:
--------------------------
|diff -ur cheese-2.26.0.orig/src/cheese-webcam.c cheese-2.26.0/src/cheese-webcam.c
|--- cheese-2.26.0.orig/src/cheese-webcam.c 2009-03-16 18:46:10.000000000 +0100
|+++ cheese-2.26.0/src/cheese-webcam.c 2009-05-11 18:35:45.960992276 +0200
--------------------------
File to patch:

What do i wrong.
P.S. i have totaly no experience with patches.

it is "-p0" not "-po" (That is a zero, not an 'oh')

---

### Post by robin.nightingale on 2009-07-01
Thanks for the Help but when i type in the right option i get the following Error.
Does Anyone know Help ?

Thanks

mogli@xxy:~/Desktop$ patch -p0 < isight.diff
can't find file to patch at input line 2
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -r cheese-2.26.0.orig/src/cheese-webcam.c cheese-2.26.0/src/cheese-webcam.c
--------------------------
File to patch:

---

### Post by tiagobt on 2009-07-01
You're probably running the patch command on the wrong folder. Try to run all the commands below, one by one, on the same system folder:

```
wget http://launchpadlibrarian.net/26667219/isight.diff
sudo apt-get install apt-src
apt-src install cheese
patch -p0 < isight.diff
apt-src build cheese
sudo dpkg -i cheese_2.26.*.deb
echo "cheese hold" | sudo dpkg --set-selections
```

---

### Post by drewjurecka on 2009-07-05
where can the patch be found?  can you post a link?

---

### Post by drewjurecka on 2009-07-05
nevermind.  I followed tiagobt's instructions and it worked perfectly.  Thanks!

---

### Post by robin.nightingale on 2009-07-19
Thanks for the how to of tiagobt.
Now the cam works perfectly from today ubuntu will be my main os.

Thanks

---

### Post by sau99ms on 2009-07-22
> **mabovo said:**
> I've applied the patch in Launchpad and green issue has gone.

Mac2,1 - Jaunty(Kernel 2.6.30-RC5).


Hi,

I'm having the same problem with my Macbook 2,1 running Jaunty only  - it's been a week and loving it(!) I'm a real newbie so could you spell out how you applied the patch. I tried the same as someone before - adding the videoscale aprt but it won't save. I really do appreciate your help - I haven't video chatted with my wife for a week because of this bug so I can't thank you enough in advance for your help.

All the best,

Mark

---

### Post by sau99ms on 2009-07-22
> **volanin said:**
> Thank you!
To avoid the system-updater annoyance, just:

```
$ sudo aptitude hold lib32v4l-0 libv4l-0
$ echo "lib32v4l-0 hold" | sudo dpkg --set-selections
$ echo "libv4l-0 hold" | sudo dpkg --set-selections

```

Hi again,

Can someone help and tell me where I'm going in. I copied and pasted this into my terminal and it didn't work after trying cheese. Am I right in thinking that I need to enter something instead of the 'Set Selections' part in the code. If so - what do I enter here? I have to say it's not entirely obvious so some clarification would really be appreciated!

Thanks,

Mark A. N. Ewbie :)

---

### Post by tiagobt on 2009-07-22
> **sau99ms said:**
> Hi again,

Can someone help and tell me where I'm going in. I copied and pasted this into my terminal and it didn't work after trying cheese. Am I right in thinking that I need to enter something instead of the 'Set Selections' part in the code. If so - what do I enter here? I have to say it's not entirely obvious so some clarification would really be appreciated!

Thanks,

Mark A. N. Ewbie :)

Did you try the instructions I sent some posts ago?

Notice, however, that the patch only works with Cheese. If you want iSight to work with all programs, you have to revert the webcam driver. Take a look at the following instructions:

[https://help.ubuntu.com/community/MacBook2-1/Jaunty#iSight](https://help.ubuntu.com/community/MacBook2-1/Jaunty#iSight)

---

### Post by Rog-Mahal on 2009-07-24
It might be helpful for 64 bit users to know that they have to downgrade the lib32v4l package as well in order for some programs to work (and to keep the update manager from bugging you that a package is broken). You can find it [here.]("http://packages.ubuntu.com/intrepid/lib32v4l-0")I found that Cheese would work with just libv4l, but Skype required downgrading lib32v4l as well.

Hope that helps!

---

### Post by tripundra on 2009-08-08
I had the green thing.
And installing the apple-isight-firmware, plus upgrading to the Karmic libV4l  did the trick.

It now works well both with Cheese, Skype, you name it!

Here goes the link!!
[http://packages.ubuntu.com/karmic/libv4l-0](http://packages.ubuntu.com/karmic/libv4l-0)

---

### Post by Rog-Mahal on 2009-08-09
Good to know that they fixed it for the upcoming release. Thanks for the info!

---

