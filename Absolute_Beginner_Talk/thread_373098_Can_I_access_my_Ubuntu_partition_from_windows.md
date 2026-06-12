---
title: "Can I access my Ubuntu partition from windows?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2007-02-28
Hello - 

I have a dual boot setup - Master IDE has grub and ubuntu, and i have XP on the Slave IDE - my dual-disk dual-boot works great.

Also, I have mounted my windows partion in ubuntu, so I can access my entire windows drive(ntfs)  from with ubuntu.

Now the question - How can I do the same from XP, to access my ubuntu drive? Even if it means installing 3rd party software etc, i would like to have this feature.

thanks for any help-
Jon

---

### Post by 23meg on 2007-02-28
Yes, you can with this:

[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by tubasoldier on 2007-02-28
Yes, you can. You have a few options:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Someone else may have more information about it. I don't really know how well it works since I don't have windows. So good luck with all that!

---

### Post by 23meg on 2007-02-28
EXT2IFS is very reliable. I wouldn't hesitate to recommend it.

---

### Post by haricharan on 2007-02-28
yes you can....

1. Goto [http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html") and download Ext2IFS_1_10c.exe
2. Install it on your windows
3. Goto Control Panel and select IFS Drives
4. Select the Drive Letter for your ext2 or ext3 partition
5. You got your partition in My Computer :)

---

### Post by alienexplorers on 2007-02-28
EXT2IFS is a very good program for letting you access Linux files from windows.

---

### Post by jondecker76 on 2007-03-01
Thanks guys - worked great!

---

### Post by Neobuntu on 2007-03-01
Why would you want the security nightmare Windows, enabled to access your Linux partitions?

There's something to be said for keeping them separate. Experienced users don't even like Windows access enabled (unless it's a repair CD) so one system doesn't affect the other.

Why not use a flash drive, get what you need and leave Windows for off-line testing?

Do you what you want. FYI

IMHO, if one is a regular user, it's time to do it in Kubuntu without Windows.

Also, unless you are a developer, virtulizers by the way are not better. They can not do everything native can do and they require excessive resources. WINE is an exception for some Windows apps and works much as if they were native to Kubuntu. A dual boot is true native to each OS which may make the reboot worth the time. Yet, why not just use Kubuntu.

Different strokes but unless you have unusual needs, consult or develop, just use Kubuntu Dapper. Unless you are just experimenting.

On the other hand, dual boot Windows so you can see for yourself how much better Kubuntu has become. The point is, you'll need time to compare. If you don't have time, use Kubuntu. Windows wastes MORE time.

---

### Post by Elixer on 2008-05-26
um... windows has it's uses. like gaming, for example.

---

