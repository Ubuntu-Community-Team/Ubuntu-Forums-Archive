---
title: "Kubuntu Java Environment Adept Install"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by hannibal_smitty on 2006-11-08
I recently discovered a fix for installing Java through Adept.

The problem is that you have to accept the user agreement, and this cannot be done (through my knowledge) in the GUI interface.  This fix will even work if you have already started the install in the Adept Package Manager and are stuck in with the update problems.  In the terminal, type:

sudo apt-get install sun-java5-bin

(or search for the appropriate package using:
sudo apt-cache search java runtime)


You will get a blue screen with the user agreement.  Hit <F12> and it will prompt you to accept the agreement.  Move the cursor to the appropriate response and hit <Enter>.  It will then begin installing, and the package manager will begin to work normally again.

This also worked with the installation of the Firefox Java plugin.  I hope this can help someone!

---

### Post by Blutack on 2006-11-08
Even more funkily...if you click more details in adept you get shown the terminal window with dpkg running inside, just click in it and accept.  For those who like to keep it clicky.

---

### Post by rgeldart on 2007-02-16
Thanks a million Hannibal 

Hit <F12> was the missing info I desperately needed having been stuck for some time trying to figure out how to accept the Sun Java agreement.....JRE and plugins now working fine.

---

### Post by dabets on 2007-03-09
You could try to manually deleting the packages you downloaded. In this case sun-java-bin.deb or something like it. It should be in /var/cache/apt/archives/

Then you could try downloading again. Just a suggestion.

---

### Post by easyease on 2007-03-10
phew im glad to have found this. that problem has been bugging me for hours, its not possible to delete the files because it could break other dependencies even though the package was installed but not cleared to use. the point is, bluetack, that the blue screen   adept throws up doesnt react to any keystroke or click of mouse......
 Thanks hannibal the magic f12 advice has made my day!

---

### Post by Pepandy on 2007-03-25
> **rgeldart said:**
> Thanks a million Hannibal 

Hit <F12> was the missing info I desperately needed having been stuck for some time trying to figure out how to accept the Sun Java agreement.....JRE and plugins now working fine.

I've hit this same problem, and F12 does nothing.

How can I get out of the update and leave the state intact?

I tried to install Java a few months ago, and hit exactly this, and eventually I had to re-install the whole of Dapper and my other applications to clear the updater. Since I've put Ubuntu on another machine, and that installed Java fine, I tried it on Kubuntu again, and still no go.

I would rather not have to re-install everything yet again - it's a real pain, so anyone with any ideas on how I can accept Sun's license? Unfortunately this is on the machine I use most and has all my e-mail etc. on it. I can still work, but I guess I cannot switch it off (it's a laptop), nor can I get any further updates until I've accepted this license; but how?

---

### Post by rgeldart on 2007-03-26
Ok so F12 doesn't work for you...

I'm not sure what to suggest other than if you are stuck in adept you could try the following terminal commands to clear the half completed process.

# apt-get -f install
# dpkg --configure -a

You may need to repeat the 2nd command a number of times 

Then you should at least be able to get further updates through adept

Another couple of thoughts :-

1. I found that I could only install Java through konsole (ie. apt-get) not through adept  
2. If F12 doesn't work then maybe your keyboard setting aren't correct, try other keys such as Tab (just a thought)...

Have a look at this link too [http://help.ubuntu.com/community/Java?highlight=%28java%29]("http://help.ubuntu.com/community/Java?highlight=%28java%29")

---

### Post by Pepandy on 2007-03-26
> **rgeldart said:**
> Ok so F12 doesn't work for you...

snip...

1. I found that I could only install Java through konsole (ie. apt-get) not through adept  
2. If F12 doesn't work then maybe your keyboard setting aren't correct, try other keys such as Tab (just a thought)...

snip...


Solved it at last. Thanks for the tips.

For the record. I had to abort adept, and then any subsequent attempts to use apt-get failed because it said the database was in use. It was not cleared by dpkg --configure -a 
except it appeared to accept a request to remove the java packages.

On the off-chance, I just rebooted, and found that I could now install Java from the command line, and all seems back to normal.

---

