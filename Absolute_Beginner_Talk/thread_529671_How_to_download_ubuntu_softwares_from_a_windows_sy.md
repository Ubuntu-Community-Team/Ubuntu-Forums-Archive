---
title: "How to download ubuntu softwares from a windows sys ?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by saurabh kakkar on 2007-08-19
hi
   I have ubuntu 7.04 on my PC and due to  limited broadband connection i m not able to download softwares and Ubuntu updates .

[SIZE="3"]I wana know Can i download ubuntu software's and updates from a windows based system like Xp and install these on 

ubuntu ?[/SIZE]

 If Yes , then plz guide me on how to do these keeping in mind that i m a noob in Linux 

also tell me r there any ubuntu software Cd's available though which i can install various software's used in ubuntu ?

---

### Post by wolfen69 on 2007-08-19
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Happy_Man on 2007-08-19
You can, although it will be a major pain. As in, nearly insane pain. 

[http://packages.ubuntu.com](http://packages.ubuntu.com) has every single application contained in the repos on it, dependencies and all. You will have to download *everything* you need manually.

But if you wish....

---

### Post by capink on 2007-08-19
If you can connect using Ubuntu briefly, do the following:

1. Update apt-get package lists:

```
sudo apt-get update
```

2. Run one of the following commands to get the urls of the packages (which one of them will depend on whether you want to download packages or upgrade your system):

```
sudo apt-get -y --print-uris install package1 package2 .....  | sed -e '/http/!d' -e s/\'// | awk '{print $1}' | sort -u > uri.txt

```

or

```
sudo apt-get -y --print-uris upgrade  | sed -e '/http/!d' -e s/\'// | awk '{print $1}' | sort -u > uri.txt

```

this will save the urls of the packages you need to download to a file called uri.txt in your current directory.

3. In Windows use your favorite download manager to download the urls int the file uri.txt

4. Now, back to Ubuntu, run either of this command (depending on what you wanted to do do at the first place):

```
sudo apt-get -o dir::cache::archives="/the/path/to/downloaded/debs/" install package1 package2 .....
```

or

```
sudo apt-get -o dir::cache::archives="/the/path/to/downloaded/debs/" upgrade
```

Note: Instead of using the -o option in step 4 you can simply place all the debs in apt cache "/var/cache/apt/archives" and run:

```
sudo apt-get install package1 package2 ......
```

or 

```
sudo apt-get upgrade
```

---

### Post by saurabh kakkar on 2007-08-21
^^ thanks buddy i will try the same and let u know

---

