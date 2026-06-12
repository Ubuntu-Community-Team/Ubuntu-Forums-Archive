---
title: "[SOLVED] Problem with TrueCrypt"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by bluewraith on 2008-02-01
Howdy everyone.. maybe someone can help. I have installed truecrypt 4.3a from the truecrypt site, as well as the GUI. Followed the instructions [here]("http://www.howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10") to the letter. Install went fine with the instructions.

I can create a new volume up the point where I select the cluster size. After that point it says 
> The TrueCrypt volume can't be created witht he selected settigns. This can have several reasons:
You have no write access for the selected directory/device
Truecrypt doesn't run as root
The volume already exists
Click at Next to create a volume or close the wizard with Exit

Now... out of those 3 reasons I can't think of one thats right. The directory I'm trying to create the volume in is my home directory, I set up truecrypt to work with sudo per the instructions, and no file exists already with that name.
When I click on "Next" (err... "Weiter" ya know...) it starts the whole shebang over again. I looked around a little bit in the forums, but I couldn't find anything related to my problem.
Thanks in advance.

---

### Post by markrad on 2008-02-01
Hmm I read your post I decided to try it myself. I only installed TrueCrypt to read a 'file' that I created on Windows and had never actually created one with the GUI.

I got exactly the same error as you reported, however I tried to mount the file afterwards and it will mount quite happily so, annoying as it is, it is actually working (for me anyway).

M.

---

### Post by bluewraith on 2008-02-01
Thats the thing though... Its not actually making a file for me to interact with... I know the GUI isn't fully stable yet, but I didn't see anything in the docs about it not being able to create a new container.

---

### Post by conehead77 on 2008-02-01
Did you also try to make a new container from the command line?

---

### Post by markrad on 2008-02-02
When I did it I did a non quick format at 16Kb and watched the format progress bar sweep across. Took a few seconds to format 200Mb. After it was done it came up with the error. Did it appear to format for you too?

---

### Post by bluewraith on 2008-02-02
I was just looking for this thread... hah, didn't think to look on page 1.

I haven't tried from command line yet. I'm fine using a command line as long as I know how to use the program, and this is a program that I haven't quite figured out yet.

I never got a progress bar or anything.

---

### Post by bluewraith on 2008-02-02
Creating a volume via command line worked. The command?
```
truecrypt -c
```
ha! Its amazing what happens when you read the manual. :)  I didn't know it had an interactive mode, and after smacking my keyboard like a retarded monkey for the random data I get it up and going.


Ok, so now that I have a container... I go back the GUI and try to mount it. Getting some problems here too... thinking I should just scrap the GUI idea and go straight command line.

From what I understand so far though, is that I have a 500MB file "test" that is my container. Now that I have that, I can mount it yet it dosn't show any mounted containers in the GUI. Also, I had to mkdir for the volume, and named it test2 since both in my home dir. Now, if its mounted do I just throw my files into test2 and then unmount?

---

### Post by bluewraith on 2008-02-02
Ok, so going on my own advice I scrapped the GUI idea. Straight commandline it was.
To make a container: (interactive mode. it asks questions, you answer)
```
truecrypt -c
```

Created a mount point for the container:
```
sudo mkdir /media/tc
```
That gave me a new folder in which to mount the container. I put it in media, just because I knew it would show on the desktop there for easy reference. Bad idea?

Mounting the container: (interactive mode again. asked for container location, where to mount it, password, and etc.)
```
truecrypt -i
```

Now then... I can throw files into the mounted container, but when I go to dismount the container it says write access has been denied. Remounting the container, and its empty.

Now what?

---

### Post by bluewraith on 2008-02-02
And now, I'm finished.
Turns out, the file system I had chosen for the container (FAT) isn't very compliant with unix permissions. Down right hates them I guess.

> The permission problem you are encountering is very common. How you mount the truecrypt volume will depend on what filesystem you selected when you created the volume. I am assuming your truecrypt volume is formatted as FAT (the default in truecrypt). FAT is convenient because you can share truecrypt volumes between Linux and Windows easily. However, FAT does not respect UNIX access controls so you have to fake it. Truecrypt provides the --user-mount flag to deal with this exact issue.
[http://ubuntuforums.org/archive/index.php/t-443864.html]("http://ubuntuforums.org/archive/index.php/t-443864.html")

Just another case of "search and you shall see". In this case, "truecrypt linux permissions" led me straight to an ubuntu archive. I love this place! :)

Methinks Linux and I are going to be good friends.

---

### Post by conehead77 on 2008-02-02
If you run
```
truecrypt -u <container> <mount point>
```
tc will mount the container with user privileges, so you dont have to have admin rights to write to the container.

To unmount all containers run this:
```
truecrypt -d
```
but i think you already figured that out :)

---

