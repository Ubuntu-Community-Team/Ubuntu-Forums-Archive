---
title: "i think i broke something (firefox)"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by tunads on 2005-12-19
i tried updating firefox and now it wont start at all.  i can't use the browers and am stuck without web access.  can someone help reconsile my current situation and help me get the new version of firefox (1.5)?

---

### Post by Evil Whisper on 2005-12-19
I'm not quite sure how you broke your firefox but you can try opening a console and typing this:

```

sudo apt-get remove mozilla-firefox

```

Next after that finishes type this in your console:

```

sudo apt-get install mozilla-firefox

```

As for installing firefox 1.5 here's how I did it:

goto [http://www.mozilla.com/](http://www.mozilla.com/) and download the tar.gz package to your desktop.

Go into your console and type this:
```

cd ~/Desktop/

```

Then type this in your console this will unpack the file:

```

tar xvf firefox-1.5.tar.gz

```

Then type this in your console this will move the newly unpacked firefox folder into the /opt/ directory:
```

sudo mv firefox /opt/

```

After you've done that type this in your console this will backup the existing symbolic link:
```

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

```

Then after you've done that type this to create the new symbolic link:
```

sudo ln -s /opt/firefox/firefox /usr/bin/firefox

```

Now you should be all set open up firefox using the existing firefox icon and goto Help --> About Mozilla Firefox and it should say version: 1.5

Hope this helps,
- Evil Whisper

---

### Post by tunads on 2005-12-19
it seemed like the first stuff worked its just that its not upgrading to 1.5

this is what happened:

***:~/Desktop$ sudo mv firefox /opt/
mv: cannot overwrite directory `/opt/firefox'
***:~/Desktop$ sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
Leaving `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
***:~/Desktop$ sudo ln -s /opt/firefox/firefox /usr/bin/firefox
ln: `/usr/bin/firefox': File exists

---

### Post by Evil Whisper on 2005-12-19
You can try doing this:

```

sudo mv /usr/bin/firefox /usr/bin/firefox-backup

```

Then remake the symbolic link:
```

sudo ln -s /opt/firefox/firefox /usr/bin/firefox

```

also what happens when you do this?
```

cd /opt/firefox/

```

Then:
```

./firefox

```

---

### Post by tunads on 2005-12-19
there's an error:

***:~$ sudo mv /usr/bin/firefox /usr/bin/firefox-backup
Password:
***:~$ sudo ln -s /opt/firefox/firefox /usr/bin/firefox
***:~$ cd /opt/firefox/
***:/opt/firefox$ ./firefox
./firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by towsonu2003 on 2005-12-25
```
sudo apt-get install libstdc++5
``` then try again

---

### Post by rizzyc on 2005-12-29
Ok I broke my firefox as well when trying to update to 1.5 so I will try this and let you know the results.

---

### Post by rizzyc on 2005-12-29
yaay I got my firefox working again AND i got it upgraded thanks for all the help!! :D
I am starting to like linux and Amsn is great.
Now i just need to find out how to add a custom shorctut for amsn w/o having to run it from the terminal all the time.

---

