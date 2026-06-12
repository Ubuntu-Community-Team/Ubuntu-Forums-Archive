---
title: "Insallation Issue"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by jonb226 on 2007-03-06
I am trying to install Ubuntu on a laptop, and I get to the part of the installation process where I have the choices of resizing the existing partition and creating an Ubuntu partition; clearing the hard drive and installing Ubuntu; the install in free space option; and the manual editing of the partition option.

I've tried to have the installer resize the existing partition many times, and it has not worked. I have not defragged the hard drive or anything because I do not know how. 

When I try to use Gparted to shrink the existing partition (there's only one partition and its for windows xp), there are problems as well. The first time I tried, the windows partition was locked, and I didn't even have the option of reizing it. The second try, I had the option of resizing it. I went through the steps to shrink it, and when I hit the button to apply the changes, there was an error. 

I was hoping to create some free space and use the third installer option (use the free space), but the windows partition uses the whole hard drive, and I can't shrink it. The first option does not work, and I don't want to delete the windows partition. Could somebody explain what they think I should do?

---

### Post by Kateikyoushi on 2007-03-06
Try to checkdisk then defragment the windows partition. If still a no go the gparted live disc is also an option. [LINK]("http://gparted.sourceforge.net/livecd.php")

---

### Post by jonb226 on 2007-03-06
How do I defrag the disk?

---

