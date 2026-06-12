---
title: "Importing mail from Win XP Thunderbird to Feisty TB (mail was originally in Eudora)"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-08-15
I want to move all my e-mail, which is in Eudora on Windows, and move it to Feisty/Thunderbird.

Someone has written in a previous Ubuntu forum posting:

----------------------

The way I migrated to Linux involved first importing my Eudora mail in Thunderbird/Windows, then copying it to Thunderbird/Ubuntu. 

-----------------------

So I too hope to move my Eudora mail to Thunderbird/Windows, and from there to Thunderbird/Ubuntu.

My question is, that I am using an old version of Eudora Light, which only allows one e-mail profile per version of the program. I have seven different e-mail profiles, so for years I've been maintaining seven separate versions of Eudora Light in my Win XP.

I tried doing the import a few days ago, and Win TB only seemed to want to import a single Eudora profile into it. Then it felt it had finished its importing work. So I thought of a plan to get all seven into TB. 

I am thinking to import each one into a fresh version of TB, so I'll end up with seven versions of TB in XP each with a single profile in it. I'll download TB seven times off the web, and each time it will import another of the seven Eudora accounts. Each time another Eudora e-mail profile (account) has been imported, I'll remove that Eudora profile to an external hard-drive along with the TB version that imported it, so the next download of TB will not be able to see that profile and will instead import one of the remaining Eudora Light profiles which still needs to be imported. In the end there will be seven profiles, each in a separate version of Win/TB. And I will copy the seven profiles and paste all seven into the /home/swarup/.mozilla-thunderbird folder in Ubuntu. Do you think it will work?

The only question I have is that, since I will never have used the TB in Windows, the application data will not be located in Windows' 
c:\Documents & Settings\user name\Application Data\Thunderbird\profiles. Where will it be? Do you know?    .

Or, if I bring back each of the 7 versions of TB onto the main hard-drive and open each one once, then will the data for all 7 profiles come to be found in that very Application Data folder?

..Many thanks!

---

### Post by swarup on 2007-08-16
Could someone kindly reply on this below message-- I really need to get this done. Anyone who has knowledge about transferring one's mail from Thunderbird/Windows to Thunderbird/Ubuntu, will be able to help. Thanks!

> **swarup said:**
> I want to move all my e-mail, which is in Eudora on Windows, and move it to Feisty/Thunderbird.

Someone has written in a previous Ubuntu forum posting:

----------------------

The way I migrated to Linux involved first importing my Eudora mail in Thunderbird/Windows, then copying it to Thunderbird/Ubuntu. 

-----------------------

So I too hope to move my Eudora mail to Thunderbird/Windows, and from there to Thunderbird/Ubuntu.

My question is, that I am using an old version of Eudora Light, which only allows one e-mail profile per version of the program. I have seven different e-mail profiles, so for years I've been maintaining seven separate versions of Eudora Light in my Win XP.

I tried doing the import a few days ago, and Win TB only seemed to want to import a single Eudora profile into it. Then it felt it had finished its importing work. So I thought of a plan to get all seven into TB. 

I am thinking to import each one into a fresh version of TB, so I'll end up with seven versions of TB in XP each with a single profile in it. I'll download TB seven times off the web, and each time it will import another of the seven Eudora accounts. Each time another Eudora e-mail profile (account) has been imported, I'll remove that Eudora profile to an external hard-drive along with the TB version that imported it, so the next download of TB will not be able to see that profile and will instead import one of the remaining Eudora Light profiles which still needs to be imported. In the end there will be seven profiles, each in a separate version of Win/TB. And I will copy the seven profiles and paste all seven into the /home/swarup/.mozilla-thunderbird folder in Ubuntu. Do you think it will work?

The only question I have is that, since I will never have used the TB in Windows, the application data will not be located in Windows' 
c:\Documents & Settings\user name\Application Data\Thunderbird\profiles. Where will it be? Do you know?    .

Or, if I bring back each of the 7 versions of TB onto the main hard-drive and open each one once, then will the data for all 7 profiles come to be found in that very Application Data folder?

..Many thanks!

---

### Post by aysiu on 2007-08-16
It **will** be in C:\Documents and Settings\*username*\Application Data\Thunderbird\Profiles, whether you use Thunderbird or not. You must have used Thunderbird at least once to get it to import from Eudora.

And I don't see the point in downloading Thunderbird seven times. It isn't a new instance of Thunderbird that will import Eudora. It's the new Thunderbird profile that will import Eudora again.

So what you should do is import one Eudora profile, move C:\Documents and Settings\*username*\Application Data\Thunderbird\Profiles to C:\Documents and Settings\*username*\Desktop\Thunderbird\Profiles and then start Thunderbird again and do the import again.

I'm speaking entirely theoretically. I don't actually have Eudora, and I haven't used it since the late 90s.

---

### Post by swarup on 2007-08-16
> **aysiu said:**
> It **will** be in C:\Documents and Settings\*username*\Application Data\Thunderbird\Profiles, whether you use Thunderbird or not. You must have used Thunderbird at least once to get it to import from Eudora.

And I don't see the point in downloading Thunderbird seven times. It isn't a new instance of Thunderbird that will import Eudora. It's the new Thunderbird profile that will import Eudora again.

So what you should do is import one Eudora profile, move C:\Documents and Settings\*username*\Application Data\Thunderbird\Profiles to C:\Documents and Settings\*username*\Desktop\Thunderbird\Profiles and then start Thunderbird again and do the import again.

I'm speaking entirely theoretically. I don't actually have Eudora, and I haven't used it since the late 90s.

I see. That is immensely helpful. 

3 points:

1. To confirm: so when I move the profiles folder from the Application Data folder to the Desktop, then close and open Thunderbird again, it will ask anew if I want to import and I can then import from another of the Eudora accounts. 

2. Do you agree that since there are seven Eudora accounts and Thunderbird does not give me the opportunity to tell it which Eudora account I want to import, then the only way to assure that it isn't going to re-import an account I've already imported, the only way is that once Thunderbird has imported a particular Eudora account, I should move that Eudora account to an external hard-drive so Thunderbird will not be able to see it the next time round, and will import one of the remaining Eudora accounts which it has not yet imported.  ---Or is there a quicker, more intelligent way to accomplish this i.e. is there a way to TELL Thunderbird WHICH Eudora account I want it to import?

3. When I move the profiles folder from Application Data folder to the Desktop, is it the entire profiles folder itself which I should move? Or should I open the profiles folder and move that folder which is  "a combination of letters & numbers.default" i.e. "36owge9f.default"? That I believe is the folder which contains all the info for a particular profile, isn't it? Perhaps it doesn't matter whether I move the entire profile folder or not-- I just wanted to confirm.

Many thanks.

---

### Post by swarup on 2007-08-16
I had installed Thunderbird a few weeks ago in my Win XP, and imported the data from one Eudora account to test if it would import properly. It imported fine. So today, when I was ready to do the true final imports which I would bring to Ubuntu, I went into the Thunderbird folder (in Data Applications) and deleted the profile in the profile folder since it was from several weeks back, and I wanted to import a fresh copy. But once I deleted that, then Thunderbird would not open. It would just give the error message:

"Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process or restart your system." 

But actually there was no Thunderbird running. 

So ultimately I went into Add-Remove Programs and deleted Thunderbird from the system. And then reloaded it afresh. But STILL even the new version of Thunderbird will not open, and just gives the same error message you see above. Even though there is no Thunderbird already running. I have confirmed in the list of running proceses, and there is no Thunderbird running.

So what should I do to get Thunderbird to open, so I can import my Eudora mailboxes and bring them into Thunderbird/Ubuntu?

---

