---
title: "[SOLVED] Java SE Development Kit 6"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Fanin on 2008-04-16
could someone please help me with "Java SE Development Kit 6"
i am a bit interested in learning to program in Java and i am an unexperienced programmer (noob) and i am being told to install "Java SE Development Kit 6"
i have installed Eclipse and it says "Error creating the view.  java.lang.NullPointerException" on startup
does anyone know what that means?
does it have something to do with Ubuntu or anything like that?
please help :(

PS. I'm also a complete noob at Ubuntu :)

Oh.. and how can i get NetBeans for Ubuntu?

---

### Post by Fanin on 2008-04-16
bump :KS

---

### Post by lbotha on 2008-04-16
sudo apt-get install sun-java6-jdk

There is no .deb package for netbeans 6 (The newest release), you'll have to download it from

[http://download.netbeans.org/netbeans/6.0/final/]("http://download.netbeans.org/netbeans/6.0/final/")

---

### Post by Fanin on 2008-04-16
> **lbotha said:**
> sudo apt-get install sun-java6-jdk

There is no .deb package for netbeans 6 (The newest release), you'll have to download it from

[http://download.netbeans.org/netbeans/6.0/final/]("http://download.netbeans.org/netbeans/6.0/final/")

it said "Couldn't find package sun-java6-jdk"
and after downloading from that website it says "Could not open the file /home/Fanin/Desktop/netb…-6.0.1-ml-javase-linux.sh"

---

### Post by lbotha on 2008-04-16
open your /etc/apt/sources.list file and make sure the lines specifying the repositories are not commented out, (should not start with a #).

Then, run 
sudo aptitude update

and try installing java again

About Netbeans, you have to run the install script from a terminal with 
./<filename>

---

### Post by Fanin on 2008-04-16
"Couldn't find package sun-java6-jdk" again

i tried typing sh "dir/netbeans"
remember.. i am a complete noob, even at the terminal :(
is the sh command right?

---

### Post by lbotha on 2008-04-17
Ok...lets try java without a terminal...

Go to System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and place a check mark in front of all the lines except the last one, Sources code and the CDROM. Close it and hit Refresh. Now, in the Search window, type java and look for sun-java6-sdk, sun-java6-bin, and sun-java6-plugin, mark them for installation, and click Apply

For netbeans, you need to be in the directory you downloaded it in. Use the 'cd' (change directory) command to get to the right directory. When you type 'ls', you should see the netbeans script's name inside the directory. 

Now, just type
```
./<filename>
```
if that doesn't work, you might want to try typing the following first:
```
chmod a+x <filename>
```

If this still doesn't work, you can try to install netbeans 5.5 from synaptic as described above.

---

### Post by stchman on 2008-04-17
> **Fanin said:**
> could someone please help me with "Java SE Development Kit 6"
i am a bit interested in learning to program in Java and i am an unexperienced programmer (noob) and i am being told to install "Java SE Development Kit 6"
i have installed Eclipse and it says "Error creating the view.  java.lang.NullPointerException" on startup
does anyone know what that means?
does it have something to do with Ubuntu or anything like that?
please help :(

PS. I'm also a complete noob at Ubuntu :)

Oh.. and how can i get NetBeans for Ubuntu?

TO install the complete Java do this:

```

sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

Make sure all the repos are enabled.

Netbeans 5.5 and Eclipse are in the repos for Gutsy and earlier.

Netbeans 6 is in the Hardy repos.

---

### Post by Fanin on 2008-04-17
the Java problem is all set and works :)

but the NetBeans program doesn't work. i "cd" to its dir and type ./netbeans-5_5-linux.bin and it says "Permission Denied" and if i type sudo sh ./netbeans-5_5-linux.bin it says:

The launcher "netbeans-5_5-linux.bin" 
is not executable for the current user.  Please give 
execute permission for the current user before 
attempting to launch the installer.

how do i get executable permission?

---

### Post by lbotha on 2008-04-17
try this:
```
su
```

then

```
chmod a+x <filename>
```

then

```
./<filename>
```

---

### Post by Fanin on 2008-04-17
su says: "su: Authentication failure"

but after typing the other 2 cmd's it worked :D
thanks

---

### Post by stchman on 2008-04-17
> **Fanin said:**
> the Java problem is all set and works :)

but the NetBeans program doesn't work. i "cd" to its dir and type ./netbeans-5_5-linux.bin and it says "Permission Denied" and if i type sudo sh ./netbeans-5_5-linux.bin it says:

The launcher "netbeans-5_5-linux.bin" 
is not executable for the current user.  Please give 
execute permission for the current user before 
attempting to launch the installer.

how do i get executable permission?

Netbeans 5.5 is in the repos.

```
sudo apt-get install netbeans5.5
```

---

### Post by Fanin on 2008-04-17
i downloaded netbeans5.5 from their website and it works like a charm, but thanks though :)

---

### Post by lbotha on 2008-04-17
Netbeans 6 is way better than 5.5, truely awesome.

I'd definitely recommend it.

Happy programming

---

