---
title: "G Mail notifier"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by smoaky on 2007-05-09
I am a Ubuntu noob :redface:  so I need an easy to install and configure Gmail email notifier.[-o< 
It needs to sit in the panel and notify me of new email using sounds and visual notification.
I have GMAIL NOTIFY installed but cannot get it to run automatically  when I log on, I go to applications>internet>GMail Notify to start it. After that I can get no sound to notify me of any new emails. Please help me fix this if possible. Gmail Notify config does not have a sound option.
If anyone has a real good Gmail notifier besides the one I mentioned above and I can install it easily and run it automatically, let me know!!
I can't wait for CNR plug-in coming in mid june. That will make installing and running apps so much easier for Ubuntu noob's.\\:D/ 
Thanks for any possible solution:)

---

### Post by Kobalt on 2007-05-09
I use checkgmail (it in the repos, you can install it with synaptic), which you can configure to play a sound on new mail arrival. 
To launch a program at startup add it to System > Pref. > Session : programs at startup. For checkgmail simply use the command *checkgmail*.

---

### Post by Cypher on 2007-05-09
I'm curious, does the standalone GMail notifier or Checkgmail open your Gmail within itself or does it spawn Firefox? If the latter, then why not use the Firefox gmail notifier extension??

---

### Post by Kobalt on 2007-05-09
> **Cypher said:**
> I'm curious, does the standalone GMail notifier or Checkgmail open your Gmail within itself or does it spawn Firefox? If the latter, then why not use the Firefox gmail notifier extension??
I'm not sure about Gmail notifier (though it's 90% sure) but you only get the sender, the object and the first words of your email, not the whole email. Once you click the notifier it launches Firefox and get you to your inbox. This is for checkgmail and Gmail Notifier.

I don't use the Firefox extension because I don't always have it open while I'm working...

---

### Post by smoaky on 2007-05-09
Thanks Kobalt,
I got it up and running but cannot figure out how to set up sound notifications under prefrences.

---

### Post by Kobalt on 2007-05-09
In the Pref. menu, there is a field for Command to run at new mail. Enter this ```
play /path-to-your-sound
```

---

### Post by Inxsible on 2007-05-09
If getting to the mail is what you want.....why not use Evolution or Thunderbird2 to simply download the email ?
 
You can also set the frequency at which the clients check the GMail servers

---

### Post by smoaky on 2007-05-09
Great 
I have the code like this      play / phone.wav    is this correct?
Pardon my ignorance, I'm learning everyday.

---

### Post by Kobalt on 2007-05-09
Where is your phone.wav file located ? In your personal folder ? If so, it should be something like this :* play /home/$USER/phone.wav*

---

### Post by smoaky on 2007-05-09
No,
it is just one of the standard sounds that come with Ubuntu but me diving in unknown open source waters have no clue how to set up a sound to put into that command.
I have only been running Feisty for as few days now and just learning to crawl before I can walk.
Sorry to get you involved in what probably to you is quite a simple proceedure.

---

### Post by Kobalt on 2007-05-09
Where/how did you find this file ? what you need to do is to type in the full path to the phone.wav file... I believe this file is located in /usr/share/sounds so your command to execute at mail arrival would be ```
play /usr/share/sounds/phone.wav
```

---

### Post by smoaky on 2007-05-09
Yes that is the sound I just didn't know how to find it again
this is exactly how i have the command to execute on new mail
play /usr/share/sounds/phone.wav    I still have no sound. do I need to put spaces between slashes? do I replace"usr" with my logon name?
(as his face turns red with embarrasement)

---

### Post by Kobalt on 2007-05-09
You may need to install sox in order to have this command line working : ```
sudo apt-get install sox
```

PS: /usr is a folder, it's not corresponding to your username

---

### Post by smoaky on 2007-05-09
installed sox...still no email sound =[
this is exactly how I have the command

play/usr/share/sounds/phone.wav

is this correct? should there be spaces between the slashes?

---

### Post by Kobalt on 2007-05-09
it should be : > play /usr/share/sounds/phone.wav
There must be a space between play and the path to the file, nowhere else.

---

### Post by smoaky on 2007-05-09
created space between play and the path, still no sound. Yes my  volume is on and set very loud.
How in the world can something as simple as this be so difficult for me to comprehend?
My unfamiliarity with Ubuntu is what I will blame it on not my complete stupidity. At least that Is what I will keep telling myself over and over...lol

---

### Post by smoaky on 2007-05-09
OK I think I have it working because I hear the sound but I have a white screen and can't get back to my desktop. Initially when I installed Ubuntu I could only get 600x800 resolution so I enabled NVIDIA enhanced driver (something) I can't remember what it is called so I could use 1024x768. A few minutes ago I turned off the NVIDIA thingie...don't ask me why, and now when I log on all I get is a white screen and have no idea how to resolve this snafu I created =(
Help

---

### Post by smoaky on 2007-05-09
NVIDIA restricted driver____ is what it is called I belive

---

### Post by Kobalt on 2007-05-10
You need to boot and when you get to this blank screen, press Ctrl+Alt+F1, log in. You need to set the driver to "nvidia" again. To do this, enter this command line : ```
sudo nvidia-xconfig
```
Press Ctrl+Alt+Backspace to restart X and reboot (if you're still in command line simply enter *reboot*).

---

### Post by smoaky on 2007-05-10
Thank you Kobalt
I must have done something incorrect because after entering the command line sudo nvidia-xconfig
I rebooted and I get this. "Failed to start X server. It is likely not set up correctly"
Now what?

---

### Post by MyR on 2007-05-24
> **Cypher said:**
> I'm curious, does the standalone GMail notifier or Checkgmail open your Gmail within itself or does it spawn Firefox?

checkgmail can display your mail (and mark as read, archive, etc.), as well as open it in your browser

---

### Post by orb9220 on 2007-05-24
> checkgmail can display your mail (and mark as read, archive, etc.), as well as open it in your browser

Not if you are running beryl. There is a bug and author can't fix it because it is in the python or GTK libraries? It will still take you to your inbox but clicking other items on popup does not work.

Also for custom sounds I just copy from windows media folder the notify.wav and place in my home folder. Then use the aplay command. 

To have it play a number of times then I just enter the command in prefs **aplay notify.wav notify.wav notify.wav**

Works like a champ.

---

### Post by smoaky on 2007-05-24
"Also for custom sounds I just copy from windows media folder the notify.wav and place in my home folder. Then use the aplay command."

Sounds cool but I am a noob and continually learning how do I do that? In simple terms please.

---

### Post by orb9220 on 2007-05-24
Well if you copy the whole folder then you have to path to sound.

aplay /home/media/notify.wav (path to the wav file)
It is easier to just copy the wav to home which for me is orb/
Then all I do is **aplay notify.wav notify.wav notify.wav **to play it 3 times.
In your case you would have to aplay /home/media/notify.wav  /home/media/notify.wav ?

I just have **aplay notify.wav notify.wav notify.wav** in prefs command for** Command to execute on new mail**

---

### Post by MyR on 2007-05-24
> **orb9220 said:**
> Not if you are running beryl. There is a bug and author can't fix it because it is in the python or GTK libraries? It will still take you to your inbox but clicking other items on popup does not work.

the author has fixed the issue. download the latest version (1.11.1.pre3 or later) and give it a try. the package in the ubuntu repositories is outdated. I'm using beryl and it works great!

---

### Post by drowner on 2007-05-24
speaking of gmail notify, does anyone know how to change the default colours of the popup notifier? By default it uses a white background and the user system default text, which on my computer, is white.

You can see the difficulties here ;)

---

### Post by MyR on 2007-05-24
> **drowner said:**
> speaking of gmail notify, does anyone know how to change the default colours of the popup notifier? By default it uses a white background and the user system default text, which on my computer, is white.

I also had this problem, and luckily the developer has fixed this issue as well!
download the latest version
go to:
[http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail?view=log](http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail?view=log)
next to revision 8 right click on download and save target as..
remove the file extension from the name, make the file executable, and cp the file to /usr/bin/checkgmail

---

### Post by drowner on 2007-05-24
help me out with the 'make it executable' bit

---

### Post by MyR on 2007-05-24
well, graphically you can right click on it, click properties,  then click permissions and check "allow executing file as a program"

---

### Post by drowner on 2007-05-24
> **MyR said:**
> I also had this problem, and luckily the developer has fixed this issue as well!
download the latest version
go to:
[http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail?view=log](http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail?view=log)
next to revision 8 right click on download and save target as..
remove the file extension from the name, make the file executable, and cp the file to /usr/bin/checkgmail

wait
thats not gmail notify!

sorry, wrong program

---

### Post by MyR on 2007-05-24
checkgmail is a lot more functional than gmail notify. sorry, i didn't know which one you were talking about

---

### Post by drowner on 2007-05-24
checkgmail is not in the repos is it?

---

### Post by MyR on 2007-05-24
> **drowner said:**
> checkgmail is not in the repos is it?

it is. 
```
sudo aptitude install checkgmail
```
after installing, follow my instructions for replacing it with the lastest version from [http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail?view=log](http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail?view=log)

---

### Post by drowner on 2007-05-24
done.

its better ;)

is there anyway to completely change the notification colours?

---

### Post by MyR on 2007-05-24
> **drowner said:**
> is there anyway to completely change the notification colours?

not without editing the code ;] although the developer does have plans to integrate it with people's themes.

---

