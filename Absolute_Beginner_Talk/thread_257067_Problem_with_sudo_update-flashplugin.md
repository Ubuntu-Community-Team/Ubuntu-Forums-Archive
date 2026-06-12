---
title: "Problem with sudo update-flashplugin"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by itchanddino on 2006-09-14
This was working for me last week, but I had problems and I had to reinstall. 
All my repositories are up to date.  So, I installed the plugin as per ubuntuguide like I did last time, and everything is fine.  But I do the next step (sudo update-flashplugin) and I get the message 
automatic installation failed due to network problems or upstream changes
Now, I had my roommate, who also runs ubuntu, run this command and he got the same error.  It has worked for him in the past also.  Is there any way to fix this?  Thanks!

---

### Post by Carbonfish on 2006-09-14
I am not sure, but if I am understanding you right it sounds like the server might be down or there might be a network problem with that repository. It happens sometimes and usually just requires a bit of a wait.

Of course, I could be all wet and it may be something completely different. In which case, I am sure that someone helpful will be along soon.

KC

---

### Post by itchanddino on 2006-09-14
Ah, it better get fixed soon, I need youtube!

---

### Post by itchanddino on 2006-09-14
I looked at the script and this is the part that gives me the error message:

			# failed
			if [ $FAIL = "true" ]; then
				echo "automatic installation failed due to network problems or upstream changes"
				rm -rf "$UNPACKDIR"
				exit -1
			fi

But there are so many mirrors, how are all of them failing?  Is there any way to edit this script so that I can get flash back?  Thanks!

---

### Post by itchanddino on 2006-09-16
Ah!  I'm sick of this, I have flashplugin-nonfree installed, but update-flashplugin still gives me the same error.  I still can't see flash. Is there any way I can fix this?

---

### Post by Carbonfish on 2006-09-16
Hi itchanddino,

I am sorry that this problem is persisting for you. I have tried to follow the same process and have had the same result as you, although I am able to view *some* flash content.

While the flash plugin installed fine on my machine, the update-flashplugin resulted in the upstream or network error.

I don't know what the problem is, but I hope that someone can help you solve it soon (I am interested in the answer myself).

I am sorry that I couldn't be more help.

Good luck,

KC

---

### Post by seijuro on 2006-10-03
I ran into the same problem and after getting no where googling for answers I finally stumbled across a solution. Its quite easy to manually install the mozilla/compatable plugin if you go [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") just download the file unpack it run flashplayer-installer and follow the directions. Hope this helps.

---

