---
title: "[SOLVED] Trouble converting .rpm files into .deb files with Alien"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-07-19
I've searched and cannot find what I am looking for in any threads. Here is the problem. I am trying to convert a .rpm file into a .deb file using Alien. I am using the following instructions. To pre-answer any possible questions regarding these, yes, Alien is installed and so is build-essential.

Here are the rules I am following:
[COLOR=Red][COLOR=DarkGreen]Convert the package.rpm into a package.deb[/COLOR]
sudo alien -d <package-name.rpm>[/COLOR]

I get this reply from Terminal.
[COLOR=Red]kittyhawk63@kittyhawk63:~/Desktop$ sudo alien -d jre-6u2-linux-i586-rpm.bin
Unknown type of package, jre-6u2-linux-i586-rpm.bin.
kittyhawk63@kittyhawk63:~/Desktop$ 

[COLOR=Black]I tried removing the ".bin" from the file and again running the command:
I get this reply:
[COLOR=Red]kittyhawk63@kittyhawk63:~/Desktop$ sudo alien -d jre-6u2-linux-i586-rpm
Unknown type of package, jre-6u2-linux-i586-rpm.
kittyhawk63@kittyhawk63:~/Desktop$ 

[COLOR=Black]OK. I'm stuck. Any help would be greatly appreciated.
BTW, if someone should ask, this file is from a "live" weather radar site that uses Java. This file is supposed to get the live radar to operate correctly.

Thanks for any help you can offer.
kh
[/COLOR][/COLOR]

[/COLOR][/COLOR]

---

### Post by Malibu Illusion on 2007-07-19
Here's a novel idea: why not compile it from source properly? :P

---

### Post by kittyhawk63 on 2007-07-19
> **Malibu Illusion said:**
> Here's a novel idea: why not compile it from source properly? :P

And smarty pants, just how would I do that?  Tit for tat.

---

### Post by aysiu on 2007-07-19
Isn't a native .deb for Java already in the Ubuntu repositories?

---

### Post by Majorix on 2007-07-19
You are not converting a .rpm file. You are trying to convert a .bin file, which will result in errors.

If I remember correctly, you first have to run the .bin file of the Java installer which will result in an rpm file. Then you can convert that.

Hope it helps.

---

### Post by kittyhawk63 on 2007-07-19
> **aysiu said:**
> Isn't a native .deb for Java already in the Ubuntu repositories?

I don't know. There were so many files on java that I had no idea which to choose. That is why I am going with this method.
kh

---

### Post by Outrunner on 2007-07-19
You're trying to install java right? Why not just open Synaptic and search for 'sun-java'

---

### Post by kittyhawk63 on 2007-07-19
Without being rerouted, can I get help on the question as submitted?
kh

---

### Post by Majorix on 2007-07-19
There is Java on the repos. But it is somewhat outdated. If you want to just browse Java applets, you need sun-java6-plugin. If you want to also develop Java then you need sun-java6-sdk.

---

### Post by kittyhawk63 on 2007-07-19
> **Outrunner said:**
> You're trying to install java right? Why not just open Synaptic and search for 'sun-java'

Will any java work to accomplish this?

---

### Post by kittyhawk63 on 2007-07-19
> **Majorix said:**
> There is Java on the repos. But it is somewhat outdated. If you want to just browse Java applets, you need sun-java6-plugin. If you want to also develop Java then you need sun-java6-sdk.

Thank you for this suggestion.

---

### Post by Outrunner on 2007-07-19
> **kittyhawk63 said:**
> Without being rerouted, can I get help on the question as submitted?
kh

Sure, but there's not much point. Using this would be faster

```
sudo apt-get install sun-java6-jre
```

---

### Post by Majorix on 2007-07-19
Why are you ignoring my posts? :-k

Oh you replied sorry. Ignore this post instead :D

---

### Post by kittyhawk63 on 2007-07-19
> **Majorix said:**
> Why are you ignoring my posts? :-k

Oh you replied sorry. Ignore this post instead :D

I'm not, just now getting to yours.
Sorry if it seemed that way. I am looking at all responses.
kh

---

### Post by kittyhawk63 on 2007-07-19
Does anyone want to tackle the thread as originally posted?

P.S. I will try the suggested java scripts in repo.
kh

---

### Post by kittyhawk63 on 2007-07-19
> **Outrunner said:**
> Sure, but there's not much point. Using this would be faster

```
sudo apt-get install sun-java6-jre
```

Done. Thanks

[COLOR=Red] Edit: That java script is already installed and it does not help on the radar weather site.[/COLOR]
kh

---

### Post by aysiu on 2007-07-19
I think pasting this command in the terminal will fix it: ```
sudo apt-get update && sudo apt-get install sun-java6-plugin
```

---

### Post by Majorix on 2007-07-19
> **kittyhawk63 said:**
> Does anyone want to tackle the thread as originally posted?

P.S. I will try the suggested java scripts in repo.
kh

My first post should answer the thread's original question. If not, post back.

---

### Post by asmoore82 on 2007-07-19
> **kittyhawk63 said:**
> Does anyone want to tackle the thread as originally posted?

P.S. I will try the suggested java scripts in repo.
kh

not really ...

Red Hat Linux: not #1 anymore for a reason!

.rpm BAD; .deb/apt/synaptic GOOD

---

### Post by kittyhawk63 on 2007-07-19
> **aysiu said:**
> I think pasting this command in the terminal will fix it: ```
sudo apt-get update && sudo apt-get install sun-java6-plugin
```

Ran this and I was already up-to-date. Thanks

---

### Post by kittyhawk63 on 2007-07-19
> **asmoore82 said:**
> not really ...

Red Hat Linux: not #1 anymore for a reason!

.rpm BAD; .deb/apt/synaptic GOOD

Ok? (with a lilted voice inflection)

---

### Post by Outrunner on 2007-07-19
If everything is up to date then I suggest exiting Firefox and restarting the Xserver. See if the site works after that.

---

### Post by kittyhawk63 on 2007-07-19
> **Majorix said:**
> You are not converting a .rpm file. You are trying to convert a .bin file, which will result in errors.

If I remember correctly, you first have to run the .bin file of the Java installer which will result in an rpm file. Then you can convert that.

Hope it helps.

Sorry, I missed this one Majorix. How do I run the .bin file to get it convert to a .rpm file?
  Thanks for your patience.
kh

---

### Post by kittyhawk63 on 2007-07-19
> **Outrunner said:**
> If everything is up to date then I suggest exiting Firefox and restarting the Xserver. See if the site works after that.

Done rebooting several times. Thanks for your suggestion.
kh

---

### Post by Majorix on 2007-07-19
You don't really need to do anything if you have the Java from the repos up-to-date. Restart Firefox and see if it works.

---

### Post by Majorix on 2007-07-19
Ok is the .bin file executable?
```
chmod +x filename
```

first, then run it. It does the thing automatically.

---

### Post by kittyhawk63 on 2007-07-19
> **Majorix said:**
> You don't really need to do anything if you have the Java from the repos up-to-date. Restart Firefox and see if it works.

OK. I'll give it another try. Sometimes more than one reboot has helped me before.
kh

---

### Post by kittyhawk63 on 2007-07-19
> **Majorix said:**
> Ok is the .bin file executable?
```
chmod +x filename
```first, then run it. It does the thing automatically.

Thanks, I think this is what I was looking for.
kh

[COLOR=Red] Edit: Well, the color of the file turned from black to green in Terminal. I tried the "sudo alien -d jre-6u2-linux-i586.bin" and nothing happened. Why is it still a .bin file after running chmod?[/COLOR]
kh

---

### Post by Outrunner on 2007-07-19
> **kittyhawk63 said:**
> Sorry, I missed this one Majorix. How do I run the .bin file to get it convert to a .rpm file?
  Thanks for your patience.
kh

```
/path/to/file.bin
```

---

### Post by kittyhawk63 on 2007-07-19
> **Outrunner said:**
> Sure, but there's not much point. Using this would be faster

```
sudo apt-get install sun-java6-jre
```

This file is installed and it does not accomplish what I want it to do. Thanks anyway.

---

### Post by kittyhawk63 on 2007-07-19
> **Outrunner said:**
> ```
/path/to/file.bin
```

I don't quite understand this instruction. Can you elaborate on it somewhat?
kh

---

### Post by Outrunner on 2007-07-19
```
~/Desktop/jre-6u2-linux-i586-rpm.bin
```

I thought it was quite clear.

EDIT: How to install anything in Ubuntu - [http://monkeyblog.org/ubuntu/installing/#installer](http://monkeyblog.org/ubuntu/installing/#installer)

---

### Post by Majorix on 2007-07-19
For example, if the file is located in your home folder, then do this:
```
~/filename
```

Or if, for example, the file is located on your desktop, then do this:
```
~/Desktop/filename
```

If you are still puzzled, tell me where the file is located and I will type in the appropriate code here.

---

### Post by kittyhawk63 on 2007-07-19
> **Outrunner said:**
> ```
~/Desktop/jre-6u2-linux-i586-rpm.bin
```I thought it was quite clear.

I am sure it is if you know what it means. I really didn't know what it meant. Sorry. This is new stuff to me.

Thanks again.

kh

---

### Post by Calash on 2007-07-19
You need to run the .bin file in the terminal, that is what the commands they are posting are for.

---

### Post by kittyhawk63 on 2007-07-19
> **Majorix said:**
> For example, if the file is located in your home folder, then do this:
```
~/filename
```Or if, for example, the file is located on your desktop, then do this:
```
~/Desktop/filename
```If you are still puzzled, tell me where the file is located and I will type in the appropriate code here.


It is on my desktop. I know to enter "cd Desktop" in terminal. I ran the chmod after doing that. It still left it as a .bin file. Any suggestions on what I am doing wrong?

---

### Post by Outrunner on 2007-07-19
Check my previous post, I made an edit.

> **kittyhawk63 said:**
> It is on my desktop. I know to enter "cd Desktop" in terminal. I ran the chmod after doing that. It still left it as a .bin file. Any suggestions on what I am doing wrong?

Yes it will remain a .bin file. After you used the chmod command, type this

./*.bin

---

### Post by Majorix on 2007-07-19
It is supposed to stay as a bin file. Now what does double clicking it do?

---

### Post by kittyhawk63 on 2007-07-19
> **Outrunner said:**
> Check my previous post, I made an edit.

Thanks.

---

### Post by kittyhawk63 on 2007-07-19
> **Majorix said:**
> It is supposed to stay as a bin file. Now what does double clicking it do?

I double click and I get what is in the attachment.

---

### Post by Majorix on 2007-07-19
You are supposed to click the first file. That one is the correct file. If its executable, then there shouldn't be any problems running it.

hope it helps.

---

### Post by kittyhawk63 on 2007-07-19
If you look at my desktop you will notice I have the same file as a .rpm file. I had a similar problem installing it with Alien. Maybe it will be one step shorter than trying to work with the .bin file. What do you think?

Edit: I'm Slow. You responded already on this other file.

Edit: Double clicking it gives me the same response as in the attachment.

---

### Post by Majorix on 2007-07-19
That what you have on your desktop is NOT an rpm file. It is a bin file thats supposed to create an rpm file when executed.

First you have to set it executable if its not, then run it by double clicking it. Double clicking is not the best way to do it since you won't be able to see the errors if there are any, but its what you are used to, since you are also a Windows user.

Post back with anything.

---

### Post by Majorix on 2007-07-19
Ok the file isn't executable then.

Do this:
-Right click the bin file.
-Go to Properties.
-Open the Permisssions tab.
-Check "Allow executing as program" or whateveer that was called.

Then when you double click it it will execute.

---

### Post by kittyhawk63 on 2007-07-19
> **Majorix said:**
> That what you have on your desktop is NOT an rpm file. It is a bin file thats supposed to create an rpm file when executed.

First you have to set it executable if its not, then run it by double clicking it. Double clicking is not the best way to do it since you won't be able to see the errors if there are any, but its what you are used to, since you are also a Windows user.

Post back with anything.

OK. I made it executable. It was not checked to be executable. I will post back the results.
kh

---

### Post by Outrunner on 2007-07-19
:D Now that you have the .rpm you need to use alien to conver it to a .deb file. I'm not sure what the exact command is since I've never used alien 

Then you install the .deb file with
```

sudo dpkg -i *.deb
```

Oh and sorry about my earlier posts, I know I was rude, but you see, I'm standing in front of the computer in the dead of night, kinda easy to loose patience :-k Time for bed it seems, good luck with java

---

### Post by kittyhawk63 on 2007-07-19
Majorix,
[SIZE=5]**[COLOR=Red]Voila![/COLOR]**[/SIZE]
Got it working. Thanks for all your help. I will be sure to save this thread.
Thanks to others for their help also.

---

### Post by kittyhawk63 on 2007-07-19
> **Outrunner said:**
> :D Now that you have the .rpm you need to use alien to conver it to a .deb file. I'm not sure what the exact command is since I've never used alien 

Then you install the .deb file with
```

sudo dpkg -i *.deb
```Oh and sorry about my earlier posts, I know I was rude, but you see, I'm standing in front of the computer in the dead of night, kinda easy to loose patience :-k Time for bed it seems, good luck with java

No problem. Have a good nites rest.
kh

---

