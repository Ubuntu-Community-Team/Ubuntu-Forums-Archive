---
title: "i am having amark bug problems can anyone help"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by timetoballj on 2008-04-11
i got a bug problem with amark can anyone tell me how to fix it

---

### Post by Crafty Kisses on 2008-04-11
> **timetoballj said:**
> i got a bug problem with amark can anyone tell me how to fix it

What exactly happens? We need more details.

---

### Post by timetoballj on 2008-04-11
it said that it cant play mp3s and when i hit install the mp3 pack it closes and reopens after i try to up date my collection

---

### Post by TWO on 2008-04-11
> **timetoballj said:**
> it said that it cant play mp3s and when i hit install the mp3 pack it closes and reopens after i try to up date my collection

Are you saying that once mp3 support is installed you are unable to update your collection without the program closing itself, or are you saying that when you attempt to install mp3 support the program closes?
 
Either way, use the following how-to guide to help you to set up mp3 amongst other things on Ubuntu:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Hope that helps.

TWO

Edit: Not that it matters, you didn't mention whether you were using Kubuntu, Ubuntu or Xubuntu. Either way, make sure to follow the instructions which correspond to your flavour of Ubuntu.

---

### Post by timetoballj on 2008-04-11
> **TWO said:**
> Are you saying that once mp3 support is installed you are unable to update your collection without the program closing itself, or are you saying that when you attempt to install mp3 support the program closes?
 
Either way, use the following how-to guide to help you to set up mp3 amongst other things on Ubuntu:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Hope that helps.

TWO
the second one of the two

---

### Post by timetoballj on 2008-04-11
and that really dont get what that thread was to do to help me

---

### Post by TWO on 2008-04-11
> **timetoballj said:**
> and that really dont get what that thread was to do to help me

It was supposed to help you to install mp3 support.
I wasn't sure whether you were saying that you had installed mp3 support but then couldn't update your collection or that when you clicked to install mp3 support, the program closed.

Which one is it?

---

### Post by timetoballj on 2008-04-11
when i clicked to install the mp3 suport  the program closes and it told me there was a bug but i didi not know what i was doing and closed it

---

### Post by TWO on 2008-04-11
> **timetoballj said:**
> when i clicked to install the mp3 suport  the program closes and it told me there was a bug but i didi not know what i was doing and closed it

Do you remember what the error message was?

---

### Post by timetoballj on 2008-04-11
thats the problem no

---

### Post by TWO on 2008-04-11
Hm, OK. 

Am I right in assuming that you can access the program without any problems? In that case, then I'd suggest trying to install mp3 support separately in order to see whether that makes a difference.

The following Ubuntu community page [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) provides instructions as to how to do so. I assume that you're using Gutsy Gibbon so follow the instructions that correspond to that. If post install, you're still getting an error message. I suggest reinstalling the Amarok package and see what happens then. 

TWO

Edit: As you'll see on the page, that will install support for other formats as well as mp3.

---

### Post by timetoballj on 2008-04-11
i dont know what that page is telling me to do i have done some of that stuff to get my dvd player working before i really have no where to start and those pages make little sense to me at times

---

### Post by timetoballj on 2008-04-11
and it will start playing the music it just dont give my the control over the program to choose what to play or skip a track

---

### Post by TWO on 2008-04-11
> **timetoballj said:**
> i dont know what that page is telling me to do i have done some of that stuff to get my dvd player working before i really have no where to start and those pages make little sense to me at times

OK. Did you manage to get your DVD player to work? 

Anyway, to download the package in that link that I sent, open a Terminal- I think it's via Applications -> Accesories -> Terminal, then paste the following into the window:

> sudo apt-get install ubuntu-restricted-extras

Enter your password if prompted, and press Y if it asks for any confirmation. Let it download and then when finished, give Amarok a try and see what happens. 

TWO

---

### Post by timetoballj on 2008-04-11
its when i update the playlist collection to play the music i have that it gives me no control over the program but will play and gives me the down load mp3 thing that i have done already for amarok once it has nothing to do with the other stuff this is a problem with amarok i believe and i am sorry that i was not clear about that earlier

---

### Post by TWO on 2008-04-11
> **timetoballj said:**
> and it will start playing the music it just dont give my the control over the program to choose what to play or skip a track

Oooh right, OK that changes everything. Ignore what I just said. So if it's playing your mp3 files then you already have the support installed. Is it still prompting you to install support by any chance? 


Have you tried to install amarok again? If not, try it and see what happens. Although Amarok is not native to Ubuntu, when you install it, it should install the other packages that it needs...

TWO

Edit: I posted just after your last post so forgive me for asking the same questions again.

---

### Post by timetoballj on 2008-04-11
tried reinstall i am thing about unistall and then install again

---

### Post by TWO on 2008-04-11
> **timetoballj said:**
> its when i update the playlist collection to play the music i have that it gives me no control over the program but will play and gives me the down load mp3 thing that i have done already for amarok once it has nothing to do with the other stuff this is a problem with amarok i believe and i am sorry that i was not clear about that earlier

Sorry if this sounds too technical, but do you know which  **'Collection Database'** type you have selected under settings?

TWO

---

### Post by timetoballj on 2008-04-11
no but i am will to up to find out if it can help but the amarok program gave me bug to report

---

### Post by TWO on 2008-04-11
> **timetoballj said:**
> no but i am will to up to find out if it can help but the amarok program gave me bug to report

Are you saying the program has crashed again whilst you've been using it? Or are you talking about the original error message?

You can find the **Collection Database** under Settings -> Configure Amarok -> Collections within the program.

---

### Post by forestpixie on 2008-04-11
If you're going to try a reinstall make sure you purge it and also it might be worth deleting the hidden folder in your home folder.

Delete the folder first, I'm assuming that you are using ubuntu, don't quite know where the file will be in kubuntu - open nautilus and do Ctrl+H - you should now see your hidden folders - navigate to .kde - open that and inside that open share and then apps - youshould see a amarok folder - delete that folder.


Then reinstall 

```
sudo apt-get remove --purge amarok &&sudo apt-get install amarok
```

I had a similar problem a while back with it closing on me.

---

### Post by timetoballj on 2008-04-11
when i update that it will play but will not give me the power to skip or choose what song to play

---

### Post by forestpixie on 2008-04-11
When you ran the command did it actually work - have you got rid of the medibuntu error from your other thread?

---

### Post by timetoballj on 2008-04-11
i got this erro that needs to be fixed and i have to fix to use synaptic apt. mang. and this is it
E: Type '--02:23:17--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by timetoballj on 2008-04-11
got that fixed and no it does not work

---

### Post by forestpixie on 2008-04-11
I'm a bit confused as to what the problem is - when you started the thread it wouldn't play mp3 files - but now it does and you have no control over the files - is that correct. Are the files in the playlist by any chance greyed out? If they are do this in a terminal

```
sudo apt-get install libxine1-ffmpeg
```

If that is not the case - 

did you try deleting the folder before you ran the purge and reinstall commands? If you still have the terminal window open with the commands in it - can you paste the part after the sudo apt-get remove --purge amarok &&sudo apt-get install amarok

If you did delete the folder before you ran the command it should have wanted to reload the library - did that happen

If you did do those things try running amarok from a terminal see if there are any errors show up there.

---

### Post by TWO on 2008-04-13
Hello timetoballj

Did you manage to resolve your Amarok problem yet?

TWO

---

