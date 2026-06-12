---
title: "How do I revert back to previous version after upgrade?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by USFMD82 on 2008-01-11
I am on Gutsy, and I upgraded to 7.10, and since then I have had the Initialize Hal error as well as no internet wired or wireless, in addition it jsut runs extremely slow . I have searched the boards, tried all the fixes  such as:
Concurance = none instead of shell, ive tried changing the dl form us server to main server and back, I have  tried many other fixes but none seem to work for me. Hopefully this problem gets fixed and I cna upgrade but as much use as I got out of the 7.4 version I dont see ther beeing to much trouble 

I love Ubuntu, but I cant seem to shake this error.. so how do I revert to my previous version and will it take forever liek it did to upgrade as well am I gonna have to reconfigure everything agian, (i had alot of work to get my wireless working)

---

### Post by philinux on 2008-01-11
You'll have to reinstall I'm afraid. Did you backup your home or have it on a separate partition.

You could try the link below for known bugs. It's working a treat for me.

---

### Post by nikoPSK on 2008-01-11
> **philinux said:**
> You'll have to reinstall I'm afraid. Did you backup your home or have it on a separate partition.

You could try the link below for known bugs. It's working a treat for me.

that's what I always do. lfs all the time. It might just be a bug though.

---

### Post by bumanie on 2008-01-11
As I understand it, you cannot revert to a previous version of ubuntu if you have upgraded. Unfortunately, if you want feisty back, you will have to reinstall it and set up from scratch. If you have to reinstall, ensure you have a /root, /swap and separate /home partition. If you do reinstall, see if you can save your folder to an external device or media.
.

---

### Post by capink on 2008-01-11
Theoritically, using apt-pinning with a priority of more than 1000 for the old version might work. But reality might be different. And it would be an ugly solution.

The best thing is to backup your home (you can use tar for that) and reinstall the old version.

---

### Post by nikoPSK on 2008-01-11
if you were using a backup app you can revert everything.. though I doubt you were.

---

### Post by USFMD82 on 2008-01-11
Thanks for the feedback, Apparenlty I posted this to soon, I did find a way to fix the HAL intiialization found it in this thread here 

[http://ubuntuforums.org/showthread.php?t=583940](http://ubuntuforums.org/showthread.php?t=583940)

Now I just need to get my SD card reader working and my WiFi

---

### Post by baeckel on 2008-02-20
Would it work to replace all instances of gutsy with feisty in the /etc/apt/source.list file?

i suppose i will try that and let you know.

---

### Post by baeckel on 2008-02-20
Actually after some digging in the /etc/apt directory i  found that the file sources.list.distUpgrade contains the previous versions source list... interesting, but it doesn't matter... you're only met with a bunch of dependency errors when you cp it to the sources.list file.

welp, off to play bubble hockey

---

### Post by capink on 2008-02-21
> **baeckel said:**
> Would it work to replace all instances of gutsy with feisty in the /etc/apt/source.list file?

i suppose i will try that and let you know.

If you have a test machine and want try a downgrade, try the following:


1. Open a root subshell

```
sudo -s
```

2. Make an apt_preferences file as follows

```
cat > /etc/apt/preferences << EOF
Package: *
Pin: release v=7.04
Pin-Priority: 1001

EOF
```


3. Replace all instances of gutsy with feisty in sources.list

```
sed -i 's/gutsy/feisty/g' /etc/apt/sources.list
```

4. Try the downgrade as follows:

```
apt-get update
```

```
apt-get dist-upgrade
```

[COLOR="Red"]DISCLAIMER: THE ABOVE CAN HOSE YOUR SYSTEM. DO IT ONLY IF YOU HAVE A TEST MACHINE OR AFTER BACKING UP. IT IS JUST AN EXPERIMNET TO SEE IF YOU CAN DOWNGRADE YOUR SYSTEM. I HAVE NOT TRIED IT AND I AM NOT REPONSIBLE FOR ANY DAMAGE THAT MIGHT HAPPEN TO YOUR SYSTEM.[/COLOR]

---

