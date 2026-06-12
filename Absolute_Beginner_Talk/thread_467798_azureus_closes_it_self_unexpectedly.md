---
title: "azureus closes it self unexpectedly"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2007-06-08
I have a problem with my azureus client...

when i open it stays open for about 3 seconds and then it closes it self
and that happends every time i open it 

i tried to remove and reintall but i have the same problem

does anyone what the problem is????

---

### Post by mills on 2007-06-08
rm -rf ~/.azureus && sudo apt-get remove --purge azureus && sudo apt-get install azureus && sudo update-alternatives --config java

Then It will ask you for a number. I tried with 1.4 and 6.0(or sth like that) and didnt work, so i picked option number ONE (enter an 1) and press enter. Then start azureus
Happy downloading!

[http://ubuntuforums.org/showthread.php?t=441398](http://ubuntuforums.org/showthread.php?t=441398)

---

### Post by viciouslime on 2007-06-08
Azureus has been buggy in ubuntu since breezy. It was nearly fixed in feisty then they changed it again not long before release <sigh>.

The best thing to do is download it from the azureus site: [http://azureus.sourceforge.net/]("http://azureus.sourceforge.net/")

---

### Post by fasoulas on 2007-06-08
Thnx a lot it worked for me

---

