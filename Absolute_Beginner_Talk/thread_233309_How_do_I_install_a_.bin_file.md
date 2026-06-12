---
title: "How do I install a .bin file?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2006-08-09
I just downloaded Google Earth's Linux installer... it's a .bin file, and when I try to open it, it opens in Gedit.

Anybody know how to run a file like this?

Thanks!

-Mark

---

### Post by Fass on 2006-08-09
Go into a terminal and issue the following command in the directory where the bin file is:

```
chmod a+x name_of_file.bin
```

Then run it by writing:

```
sudo ./name_of_file.bin
```

---

### Post by mjpatey on 2006-08-09
Perfect!  Thank you.  Thread bookmarked!

-Mark

---

### Post by x64Jimbo on 2006-08-09
> **Fass said:**
> Go into a terminal and issue the following command in the directory where the bin file is:

```
chmod a+x name_of_file.bin
```

Then run it by writing:

```
sudo ./name_of_file.bin
```
You don't need admin access to run google earth. Don't run programs as admin unless you absolutely need to.

---

### Post by Fass on 2006-08-10
[QUOTE=x64Jimbo]You don't need admin access to run google earth. Don't run programs as admin unless you absolutely need to.[/QUOTE]

Most installers tend to need admin privileges, IMO; I am not familiar with google earth, so I gave generic advice.

---

### Post by x64Jimbo on 2006-08-10
You are right about installers. But just plain running a .bin program doesn't need admin access.

---

### Post by groberts1980 on 2006-08-12
Okay, stupid question. I'm very new to Ubuntu, and Linux in general, so I'll probably have lots of these.

I downloaded jdk-1_5_0_08-linux-i586.bin to the Desktop and ran the commands suggested above to install it.

Now I have a jdk1.5.0_08 folder on the Desktop. It appears to have installed it here. Can I simply move the folder? If so, where should this folder really be?

---

### Post by x64Jimbo on 2006-08-13
Unless that installer is really dumb, it should have installed all of its files into system directories and you can delete those files on your desktop.

---

### Post by u04f061 on 2006-08-13
> **groberts1980 said:**
> Okay, stupid question. I'm very new to Ubuntu, and Linux in general, so I'll probably have lots of these.

I downloaded jdk-1_5_0_08-linux-i586.bin to the Desktop and ran the commands suggested above to install it.

Now I have a jdk1.5.0_08 folder on the Desktop. It appears to have installed it here. Can I simply move the folder? If so, where should this folder really be?

i have recently installed jdk1.5_07

hey cuty where from u got release 8.hooooooooooo going tooooooooo fast!!!!!!!!!

follow this procedure to install this.
public class JavaInstall{
  static void main(Sring [] arg){
    System.out.println(" joke postponed  and guide stats.

1) add multiverse repository using  RepositoriesHowto   search in wiki.ubuntu.com or go to synaptic

2) open terminal and type 


sudo apt-get update
sudo apt-get install fakeroot java-package java-common

chmod +x [java-installer].bin

but since you have already used it to install previously, it should already be executable.

Next:

fakeroot make-jpkg [java-installer].bin

and this should generate a sun-j2dk[something].deb file. 
Next step:

sudo dpkg -i sun-j2dk[something].deb

Let us know how it works out.");

System.out.println("http://ubuntuforums.org/newreply.php? 
 eply&p=1372850"  + "acknoledge to this link");
 }
}

dear i was joking .the steps to be followed are in first println command.

hope to get every thing

---

### Post by andiii on 2006-08-17
Can anyone say how I can make .bin files executable with a double click?

They open with gedit. When I say "Open with Terminal" it doesnt work. Do I have to enter a custom command?

---

### Post by suhaib on 2006-10-12
having the same problem.  I know how to install bin files but for some strange reason it just is working!  That is, the terminal doesn't give me permission, whether i use sudo or su or not.

---

### Post by Jussi Kukkonen on 2006-10-12
It's probably not executable.

```
chmod u+x <filename>
./<filename>
```

EDIT: suhaib, I didn't realise this wasn't the start page of the thread... In any case, could you try those commands and paste the output?

---

### Post by suhaib on 2006-10-14
Lol, yeah that was the problem, I checked the permissions shortly after that post and realised.

---

### Post by Gianfranco on 2006-10-15
> **Fass said:**
> Go into a terminal and issue the following command in the directory where the bin file is:

```
chmod a+x name_of_file.bin
```

Then run it by writing:

```
sudo ./name_of_file.bin
```

Great but, how do I issue a comand where the bin file is?  Sorry I am very new.
The comand windows comes up and than what ? I put the line in and i get a reply:" file does not exist"  Of course i am in wrong place.....
Thanks...

---

### Post by gatepc on 2007-07-14
hi how do i install google earth i am a linux noob and tryed what you said it didint work i am using ubuntu 7.04 i think email me at [email]gatepc@gmail.com[/email] thanks in advance

---

### Post by TheFoe92 on 2007-07-16
Since this thread is already up, I won't start another one. How can I install .cue files, if there is a way at all? I downloaded a program, but it comes with not only a .bin file but also a .cue. I was wondering how I can install it. The program is Starcraft (a game). It is made for Windows, but it can run on WINE. Any suggestions are greatly appreciated. Thanks in advance!

---

### Post by beemzet on 2007-07-21
> **Gianfranco said:**
> Great but, how do I issue a comand where the bin file is?  Sorry I am very new.
The comand windows comes up and than what ? I put the line in and i get a reply:" file does not exist"  Of course i am in wrong place.....
Thanks...

if your files are in desktop you could use
                       **cd ~/Desktop**
or maybe,
                       **cd /home/your_name/Desktop**

just use cd to browse the files you need.

---

### Post by cherry316316 on 2007-09-22
> **beemzet said:**
> if your files are in desktop you could use
                       **cd ~/Desktop**
or maybe,
                       **cd /home/your_name/Desktop**

just use cd to browse the files you need.



the problem is , after using those commands , it install the jre in desktop and not in the folder which it is supposed to be.
and i dont know which folder i am suppose to install jre 
is it /usr/bin/ or some other

---

### Post by cherry316316 on 2007-09-22
> **u04f061 said:**
> i have recently installed jdk1.5_07

hey cuty where from u got release 8.hooooooooooo going tooooooooo fast!!!!!!!!!

follow this procedure to install this.
public class JavaInstall{
  static void main(Sring [] arg){
    System.out.println(" joke postponed  and guide stats.

1) add multiverse repository using  RepositoriesHowto   search in wiki.ubuntu.com or go to synaptic

2) open terminal and type 


sudo apt-get update
sudo apt-get install fakeroot java-package java-common

chmod +x [java-installer].bin

but since you have already used it to install previously, it should already be executable.

Next:

fakeroot make-jpkg [java-installer].bin

and this should generate a sun-j2dk[something].deb file. 
Next step:

sudo dpkg -i sun-j2dk[something].deb

Let us know how it works out.");

System.out.println("http://ubuntuforums.org/newreply.php? 
 eply&p=1372850"  + "acknoledge to this link");
 }
}

dear i was joking .the steps to be followed are in first println command.

hope to get every thing

the fakeroot make-jpkg command is not working
it says make-jpkg is not a command
i also tried combination
make-dpkg , make-kpkg 
but no use :(

---

### Post by skyviannes on 2007-10-02
> **Fass said:**
> Go into a terminal and issue the following command in the directory where the bin file is:

```
chmod a+x name_of_file.bin
```

Then run it by writing:

```
sudo ./name_of_file.bin
```
i tried to install using the commands that you put in, and it gives the following output.

"The installer is unable to run in graphical mode. Try running the installer with the -console or -silent flag."

if i try the - console on the end of the command i get the following output

"The wizard cannot continue because of the following error: Invalid command line option: console is not supported (1001) (403)
WARNING: could not delete temporary file /tmp/ismp001/8707301
WARNING: could not delete temporary file /tmp/ismp001/2268776
WARNING: could not delete temporary file /tmp/ismp001/9765387'

And the -silent flag command doesnt give any output at all

---

### Post by mysticmatrix on 2007-10-02
> **TheFoe92 said:**
> Since this thread is already up, I won't start another one. How can I install .cue files, if there is a way at all? I downloaded a program, but it comes with not only a .bin file but also a .cue. I was wondering how I can install it. The program is Starcraft (a game). It is made for Windows, but it can run on WINE. Any suggestions are greatly appreciated. Thanks in advance!

The .bin and .cue are cd image file. From were did you download this? :confused:
Is starcraft being sold as CD images? :confused:

---

### Post by ma_nkooo on 2008-05-28
> **Fass said:**
> Go into a terminal and issue the following command in the directory where the bin file is:

```
chmod a+x name_of_file.bin
```

Then run it by writing:

```
sudo ./name_of_file.bin
```thank you for sharing this info.

---

