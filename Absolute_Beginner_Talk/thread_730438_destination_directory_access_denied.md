---
title: "destination directory access denied"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by muldengold on 2008-03-20
Hi,
I'm trying to install a certain software. I have no permission to install the software in any folder whatsoever (all root owned)  except my home directory. How can I get permission? Or do you install your software in your home folder:confused:???
Thanks for your help!

---

### Post by Dr Small on 2008-03-20
You need to use Sudo.
Please read the article on the wiki, as it is fairly detailed:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Dr Small

---

### Post by muldengold on 2008-03-20
Hi Dr Small,

ok thank you, I read it. And what next? Is there a sudo command to execute a file?
Thanks.

---

### Post by Mustard on 2008-03-20
> **muldengold said:**
> Hi Dr Small,

ok thank you, I read it. And what next? Is there a sudo command to execute a file?
Thanks.

It would seem that you are floundering around in the dark a bit.  It would be best to describe what you are doing in detail to make it easier for others to help you.  

What are you  installing? 
Where did you get it from?
Why are you installing it (for what purpose)?

With the answers to these questions I would have a better idea of whether you are proceeding in the right direction.

---

### Post by freebeer on 2008-03-20
> **muldengold said:**
> Hi Dr Small,

ok thank you, I read it. And what next? Is there a sudo command to execute a file?
Thanks.

You may need to make the file executable first.  A further explanation can be found [here]("http://www.cyberciti.biz/faq/howto-unix-command-run-execute-bin-files-in-linux/").  (It's just the first one I ran across, there's probably better/clearer ones around.)

---

### Post by muldengold on 2008-03-20
Thanks for your answers.
The software is Geneious, Here the link:
 [http://www.geneious.com/default,28,download.sm](http://www.geneious.com/default,28,download.sm)

When I downloaded it it came as a .sh file. After getting help from this forum how to run the file the installer started. That's basically where I'm now.
Thanks again.

---

### Post by Mustard on 2008-03-20
> **muldengold said:**
> Thanks for your answers.
The software is Geneious, Here the link:
 [http://www.geneious.com/default,28,download.sm](http://www.geneious.com/default,28,download.sm)

When I downloaded it it came as a .sh file. After getting help from this forum how to run the file the installer started. That's basically where I'm now.
Thanks again.

Is it possible to paste the output of the install process (including the command you use to start the install) ?

---

### Post by HanaD on 2008-03-20
Use sudo bash at terminal..
but remember this gives root privilages to anyone using PC,
once you do this you would have permision to every folder,
but i suggest you install whatever you are doing and then exit the root mode.

better way to use root privalge is to Use sudo infront of the command you are using interminal, this would ask you for your password. and will give you root access,

Enjoy!

---

### Post by muldengold on 2008-03-20
Firstly it asks:

"Do you want to run "Geneious_unix_3_6_1_with_jre.sh", or display its contents?"

I can choose from:

Run in terminal / Display / Cancel / Run

Then I cklick on run and the installer proceeds how I know it from windows application. When it comes to the destination I'm denied permission as described above. Is there a way to launch the installer in a way that tell it that I have permission?

Thanks very much

---

### Post by muldengold on 2008-03-20
Thanks HanaD

the file I want to run is in /home/sandro/desktop/Geneious_unix_3_6_1_with_jre.sh

What is the sudo command to run this file?

"sudo /home/sandro/desktop/Geneious_unix_3_6_1_with_jre.sh" doesn't work.

Thanks.

---

### Post by HanaD on 2008-03-20
use this guide to understand in genral terminal and a bit of sudo command,
[http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338)


also the above command you type in isnt correct.

say 
> cd /home/sandro/desktop
                                            .... ....... (this will change the directory to desktop)..
and you woud see something like /home/sandro/desktop:~$
at this promt type 
> sudo ./Geneious_unix_3_6_1_with_jre. sh and it should install it.

I presume that you downloaded the file on desktop.... that's the reason we changed the directory to desktop earlier.

Hope this helps..
Hana

---

### Post by HanaD on 2008-03-20
.

---

### Post by muldengold on 2008-03-20
Thanks HanaD

The terminal tells me: sudo: cd: command not found.

I typed in exactly what you've suggested???????

---

### Post by muldengold on 2008-03-20
... hang on it worked. At least for /home. Then it comes up (for /sandro) that no such folder exists. Well but it does... I find Linux really tricky

---

### Post by muldengold on 2008-03-21
Perhaps my last post wasn't quite understandable

But look at this:

sandro@sandro-laptop:~$ cd /home
sandro@sandro-laptop:/home$ ls
eva  sandro
sandro@sandro-laptop:/home$ cd /sandro
bash: cd: /sandro: No such file or directory
sandro@sandro-laptop:/home$ 

it shows me (after using ls) that the folder sandro exists. But when I want to jump to it it doesn't work????
Thanks for your patience, but I'm really quite a newbie

---

### Post by freebeer on 2008-03-21
use either

```

cd sandro

```

or

```

cd /home/sandro

```

The latter being the full path name.

I also note an earlier reference to "desktop" but I imagine it's really "Desktop".  Note the capital "D".  Linux commands and filenames are case sensitive.

---

### Post by muldengold on 2008-03-21
Thank you, it worked and I've been able to install the software successfully. Thanks everyone, I've learned a lot.

---

### Post by HanaD on 2008-03-21
Please mark the thread as solved if it worked for you.

Best Regards,
Hana

---

