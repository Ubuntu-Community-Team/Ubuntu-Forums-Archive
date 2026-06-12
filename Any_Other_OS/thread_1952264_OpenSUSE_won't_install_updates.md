---
title: "OpenSUSE won't install updates"
date: 2012-04-04
forum: Any Other OS
---

### Post by aligator12 on 2012-04-04
Hi, I couldn't figure out how to join the opensuse forums, so I decided to post here, hope you don't mind. :)

Anyway, opensuse won't install updates and it gives me an error message, what should I do?

---

### Post by QIII on 2012-04-04
Are you using su to get superuser privileges and using

```
zypper update
```

?

What error messages are you getting?

You really should be able to find this on an OpenSUSE forum and it shouldn't be difficult to join.  But I won't leave you in the rain this one time.  ;)

---

### Post by lisati on 2012-04-04
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by QIII on 2012-04-04
Aligator12 --

If you usually use YaST to do your updates, use zypper in the terminal this time.  That will make it easy to cut and paste the errors.

Post it here between code tags by clicking the pound sign above the text entry box and putting your cursor between the tags before pasting.

I'm off to slumberland now, but I'll try to get back to this.

---

### Post by aligator12 on 2012-04-04
Hi guys, here is the error message I receive:

"There was a (possibly temporary) problem connecting to software source.

DETAILS
File"/repodata/repomd xml' not found on medium
'http://download.opensuse.org/distribution/11.4/repo/non-oss/'

What does this mean?

---

### Post by QIII on 2012-04-04
It probably means a server was down.  I'm able to navigate to it now.

Let me update and see if I hit the same problem.  Will probably depend on if I have some software package that you also have.

Wait one.


Edit:  I was able to update just fine.  Either the server is back up or I don't have something you have installed.  Give it another try.

---

### Post by aligator12 on 2012-04-05
> **QIII said:**
> It probably means a server was down.  I'm able to navigate to it now.

Let me update and see if I hit the same problem.  Will probably depend on if I have some software package that you also have.

Wait one.


Edit:  I was able to update just fine.  Either the server is back up or I don't have something you have installed.  Give it another try.
It has been saying that for about a month now. And I have a question, using that program is how I update security patches, right? Because that is all I want to do as it has not been updated in 3 months.

---

### Post by QIII on 2012-04-05
I just noticed something now.

OpenSUSE is now at 12.1.

How old is your install?

And I think you didn't capture the whole error.  Is that line truncated?

---

### Post by aligator12 on 2012-04-05
> **QIII said:**
> I just noticed something now.

OpenSUSE is now at 12.1.

How old is your install?
Actually I copied pasted that error message from a forum post, mine is 12.1.

---

### Post by aligator12 on 2012-04-05
And I think you didn't capture the whole error. Is that line truncated?

I don't get what this means and yes, that is the whole error.

---

### Post by QIII on 2012-04-05
OK.  I'm on 12.1.

Go to YaST and open Software Repositories.

Look down through the Enabled column and make sure that all but the Debug and Source repositories are enabled (add Debug and Source if you are developing, of course.)

Let me know how it looks.

---

### Post by QIII on 2012-04-05
Ah.  I'm being summoned.

From here, hit Refresh and select "All Autorefreshed".  If anything burps, keep track of it.

Then, jot down what you currently have enabled.  Disable all but the one that says "Updates for OpenSUSE..."

Run your updates again.  That should get most of the updates you need.

Go back and enable the ones you disabled before that.

I'll try to check by again tomorrow.

---

### Post by aligator12 on 2012-04-06
> **QIII said:**
> Ah.  I'm being summoned.

From here, hit Refresh and select "All Autorefreshed".  If anything burps, keep track of it.

Then, jot down what you currently have enabled.  Disable all but the one that says "Updates for OpenSUSE..."

Run your updates again.  That should get most of the updates you need.

Go back and enable the ones you disabled before that.

I'll try to check by again tomorrow.
Sorry about the late reply. :)

Alright I deselected everything but the update in the Software Repositories and I was able to install 3 updates, I then restarted and it now says there are 150 updates that need to be installed and when I clicked the install updates button it said some dependencies were not found for some of the 150 updates. At least we are making progress. :)

---

### Post by QIII on 2012-04-07
OK.  It seems from the thread that the problem was with the non-oss repository.  Enable the others you disabled with the exception of that  one and see what happens.

I'm still scratching my head on that one repository.

---

### Post by aligator12 on 2012-04-08
> **QIII said:**
> OK.  It seems from the thread that the problem was with the non-oss repository.  Enable the others you disabled with the exception of that  one and see what happens.

I'm still scratching my head on that one repository.
Hay, I didn't have any time to try this out today, I will try tommorow when I have more time. Thanks and please check back. :)

---

### Post by aligator12 on 2012-04-08
> **QIII said:**
> OK.  It seems from the thread that the problem was with the non-oss repository.  Enable the others you disabled with the exception of that  one and see what happens.

I'm still scratching my head on that one repository.
Hay, I disabled and then re-enabled all the software check boxes in the software respiratory except "games" and it then installed all 150 of them. :D

So what should I do about the games one?

---

### Post by boydrice on 2012-04-09
could you run zypper ref and then post the output of zypper lr?

---

### Post by aligator12 on 2012-04-11
> **boydrice said:**
> could you run zypper ref and then post the output of zypper lr?
What will running this command do?

And is my computers security at risk if I can't get the games update to work?

---

### Post by boydrice on 2012-04-11
> **aligator12 said:**
> What will running this command do?

And is my computers security at risk if I can't get the games update to work?

zypper is the command line package management tool in opensuse, think apt-get on debian distros or yum on fedora/rhel.  zypper lr will list your repos.  the reason I wanted to see the repos you have installed is in one of your posts you listed a repo for 11.4 but then in another post you said you were running 12.1.  Here is a guide on zypper as of 11.3 but most of it applies.  you can also run man zypper or zypper -h for more info.

[http://en.opensuse.org/SDB:Zypper_usage]("http://en.opensuse.org/SDB:Zypper_usage")

---

### Post by aligator12 on 2012-04-12
> **boydrice said:**
> zypper is the command line package management tool in opensuse, think apt-get on debian distros or yum on fedora/rhel.  zypper lr will list your repos.  the reason I wanted to see the repos you have installed is in one of your posts you listed a repo for 11.4 but then in another post you said you were running 12.1.  Here is a guide on zypper as of 11.3 but most of it applies.  you can also run man zypper or zypper -h for more info.

[http://en.opensuse.org/SDB:Zypper_usage]("http://en.opensuse.org/SDB:Zypper_usage")
Hi, I ran the command and it said everything was up to date (except "games" which wasn't listed).

---

### Post by aligator12 on 2012-04-12
But all security patches are up to date, does that mean I am secure or do I also need to update games to be completely secure?

---

### Post by aligator12 on 2012-04-15
So what should I do?

---

### Post by boydrice on 2012-04-16
> **aligator12 said:**
> So what should I do?

If all your packages are up to date as you stated in an earlier post then I'm not sure what you need?

---

### Post by aligator12 on 2012-04-16
> **boydrice said:**
> If all your packages are up to date as you stated in an earlier post then I'm not sure what you need?
All the packages except "games" are up to date, is it a security risk not updating the "games" packages?

---

### Post by boydrice on 2012-04-16
> **aligator12 said:**
> All the packages except "games" are up to date, is it a security risk not updating the "games" packages?

[QUOTE=aligator12]Hay, I disabled and then re-enabled all the software check boxes in the software respiratory except "games" and it then installed all 150 of them. 

So what should I do about the games one?[/QUOTE]

From what you posted previously you did not enable the games repo.  Make sure you have the games repo enabled for the version you are running and then update your system.

Please see this link: [http://en.opensuse.org/Games]("http://en.opensuse.org/Games")

Then after you update your system please have a look here [http://en.opensuse.org/Package_management]("http://en.opensuse.org/Package_management")
and here [http://en.opensuse.org/SDB:System_upgrade]("http://en.opensuse.org/SDB:System_upgrade")
good luck.

---

### Post by aligator12 on 2012-04-17
> **boydrice said:**
> From what you posted previously you did not enable the games repo.  Make sure you have the games repo enabled for the version you are running and then update your system.

Please see this link: [http://en.opensuse.org/Games]("http://en.opensuse.org/Games")

Then after you update your system please have a look here [http://en.opensuse.org/Package_management]("http://en.opensuse.org/Package_management")
and here [http://en.opensuse.org/SDB:System_upgrade]("http://en.opensuse.org/SDB:System_upgrade")
good luck.
No, I did enable the game repo, but it says something like "the server can't be found". But is updating the games vital to my system security?

---

### Post by boydrice on 2012-04-17
> **aligator12 said:**
> No, I did enable the game repo, but it says something like "the server can't be found". But is updating the games vital to my system security?

Can you reach this site? [http://download.opensuse.org/repositories/games/openSUSE_12.1/]("http://download.opensuse.org/repositories/games/openSUSE_12.1/")

It seems to me that the games repo is available.  Please check your setup.  As far as it being vital to your systems security that is a question you need to answer.  Check out opensuse's security portal on their site [http://en.opensuse.org/Portal:Security]("http://en.opensuse.org/Portal:Security").

---

### Post by aligator12 on 2012-04-17
> **boydrice said:**
> Can you reach this site? [http://download.opensuse.org/repositories/games/openSUSE_12.1/]("http://download.opensuse.org/repositories/games/openSUSE_12.1/")

It seems to me that the games repo is available.  Please check your setup.  As far as it being vital to your systems security that is a question you need to answer.  Check out opensuse's security portal on their site [http://en.opensuse.org/Portal:Security]("http://en.opensuse.org/Portal:Security").
Yes I can reach it, but the update manager can't. What should I do?

And I really don't know about if I am less secure, can hackers exploit vulnerabilities in games? I also don't play network games on it.

---

### Post by boydrice on 2012-04-18
> **aligator12 said:**
> Yes I can reach it, but the update manager can't. What should I do?

And I really don't know about if I am less secure, can hackers exploit vulnerabilities in games? I also don't play network games on it.

would you please do me the favor of posting the output zypper lr so I can see the repos you have setup?

I am not going to be the one to tell you if you are secure or not with a misconfigured repo, sorry.

---

### Post by aligator12 on 2012-04-18
Alright here is the message:

File '/repodata/repomd.xml' not found on medium 'http://download.opensuse.org/repositories/games/openSUSE_11.3/'

Abort, retry, ignore? [a/r/i/?] (a):

---

### Post by boydrice on 2012-04-18
> **aligator12 said:**
> Alright here is the message:

File '/repodata/repomd.xml' not found on medium 'http://download.opensuse.org/repositories/games/openSUSE_11.3/'

Abort, retry, ignore? [a/r/i/?] (a):

Based off that message you don't have the games repo for 12.1 enabled, you have the games repo for 11.3.  11.3 went end of life January 20th, 2012 and would be the reason why it cannot reach that repository.  Remove that repo, enable the 12.1 games repo, then update your system.

Going forward please try and provide the output that is requested of you by people trying to help you.  We could have solved this a number of posts ago if you had provided some decent information.

---

### Post by aligator12 on 2012-04-19
> Based off that message you don't have the games repo for 12.1 enabled, you have the games repo for 11.3. 11.3 went end of life January 20th, 2012 and would be the reason why it cannot reach that repository. Remove that repo, enable the 12.1 games repo, then update your system.
How do I remove that repo?

> Going forward please try and provide the output that is requested of you by people trying to help you. We could have solved this a number of posts ago if you had provided some decent information.
I am very sorry. :) But the computer I am troubleshooting is not mine and I don't have physical access all the time.

---

### Post by QIII on 2012-04-19
Open YaST.  Go to Software >> Software Repositories

Select the line 

[URL="http://download.opensuse.org/repositories/games/openSUSE_11.3/"]```
http://download.opensuse.org/repositories/games/openSUSE_11.3/
```[/URL]Click "Edit".

Edit that line and  change it to:

[URL="http://download.opensuse.org/repositories/games/openSUSE_12.1/"]```
http://download.opensuse.org/repositories/games/openSUSE_12.1/
```[/URL]

I confirmed that the URL exists.

Also change the sction of the Repostory Name from 11.3 to 12.1.

Refresh your repos.  You'll probably be asked to Trust the GPG key on that repo.  Go ahead and accept that.

---

### Post by boydrice on 2012-04-19
> **aligator12 said:**
> How do I remove that repo?


I am very sorry. :) But the computer I am troubleshooting is not mine and I don't have physical access all the time.

the link I provided earlier with instructions on how to use zypper will tell you how to add or remove repos.

[http://en.opensuse.org/SDB:Zypper_usage]("http://en.opensuse.org/SDB:Zypper_usage")

---

### Post by QIII on 2012-04-19
Nice.  Obscure instructions to what the poster sees as an obscure problem.  We're good at assuming that what makes sense to us makes sense to the uninitiated.  Would you like him to read the entire thing and sort it out?

"RTFM", we say.  That's *exactly *why we get the reputation for being arrogant Linux snobs.

---

### Post by boydrice on 2012-04-19
> **QIII said:**
> Nice.  Obscure instructions to what the poster sees as an obscure problem.  We're good at assuming that what makes sense to us makes sense to the uninitiated.  Would you like him to read the entire thing and sort it out?

"RTFM", we say.  That's *exactly *why we get the reputation for being arrogant Linux snobs.

I never said RTM to the OP nor did I assume it makes sense to him.  I did provide the OP a guide to help administer his/hers/friends system.  The instructions aren't obscure but are in fact specific to opensuse and his problem.  I don't expect the OP to read it all but the part clearly called "Removing Repositories" would be a good start.

[http://en.opensuse.org/SDB:Zypper_usage#Removing_repositories]("http://en.opensuse.org/SDB:Zypper_usage#Removing_repositories")

---

### Post by QIII on 2012-04-19
Not obscure to whom?

You and me?

Clearly the OP was not getting it.

---

### Post by Favux on 2012-04-19
I have to say enabling repositories in openSUSE wasn't a simple and straightforward task for me.  And having to google around and find the manuals didn't exactly endear openSUSE to me.  I got the job done but I still don't feel like I have a great handle on it.  Why it didn't work, after I thought I had it solved, with a relog but did work after a reboot I still don't understand.

I don't think of myself as a newbie anymore.  Clearly I'm wrong.  :)

---

### Post by boydrice on 2012-04-19
> **QIII said:**
> Not obscure to whom?

You and me?

Clearly the OP was not getting it.

Using zypper should not be thought as obscure commands for someone who has chosen to use opensuse anymore than apt is obscure for someone using a debian-based system.

---

### Post by QIII on 2012-04-19
Should it be considered obscure for you and me?.  No.  It is a skill we have learned.  I've been at this stuff for about 35 years.  I'd certainly better be able to use the command line and make sense of that sort of documentation.  I rarely use GUI tools for such things.

But given the problem and the OP's responses, it is clear that it IS obscure to him.

Deal with the OP's problem from HIS point of view, not from OURS.   

Your statement is tantamount to saying that anyone who cannot follow directions for using command line methods should not choose openSUSE.  Ignorance is dispelled by learning.  Learning takes time.  The OP has an immediate problem and asked for an answer.  A GUI solution is the quickest route to a solution for that problem.  I recognized that after his first couple of responses to my suggestion that he use zypper.

Telling someone over and over to do something in some fashion without success does not reflect on the student's ability to learn, but the teacher's ability to teach.

Rather than expecting the OP's skills at the command line to spring forth from the head of Zeus fully formed and armed for battle (yours didn't), solve the OP's immediate problem today.  Teach him to use the command line tomorrow.

---

### Post by boydrice on 2012-04-19
> **QIII said:**
> Should it be considered obscure for you and me?.  No.  It is a skill we have learned.  I've been at this stuff for about 35 years.  I'd certainly better be able to use the command line and make sense of that sort of documentation.  I rarely use GUI tools for such things.

But given the problem and the OP's responses, it is clear that it IS obscure to him.

Deal with the OP's problem from HIS point of view, not from OURS.   

Your statement is tantamount to saying that anyone who cannot follow directions for using command line methods should not choose openSUSE.  Ignorance is dispelled by learning.  Learning takes time.  The OP has an immediate problem and asked for an answer.  A GUI solution is the quickest route to a solution for that problem.  I recognized that after his first couple of responses to my suggestion that he use zypper.

Telling someone over and over to do something in some fashion without success does not reflect on the student's ability to learn, but the teacher's ability to teach.

Rather than expecting the OP's skills at the command line to spring forth from the head of Zeus fully formed and armed for battle (yours didn't), solve the OP's immediate problem today.  Teach him to use the command line tomorrow.

I not quite sure why you are so bent out of shape.  I was just trying to help the OP the way that I know how to.  

I don't currently run opensuse but I have in the past.  I used zypper as the tool to manage packages and repositories.  Even though I don't use opensuse I know enough to help the OP with his problem.  If the OP didn't want to use the methods suggested to him that is fine, he could have simply said "Thanks for the info.  I looked it over and still doesn't make sense to me.  I am uncomfortable using the terminal for such things could you provide me a GUI solution to my problem?".  Had the OP done that I would have gladly let someone more adept with Yast provide him an answer or pointed him to documentation on Yast.  

So again I'm not trying to teach the OP I am trying to help him.

---

### Post by aligator12 on 2012-04-20
> **QIII said:**
> Open YaST.  Go to Software >> Software Repositories

Select the line 

[URL="http://download.opensuse.org/repositories/games/openSUSE_11.3/"]```
http://download.opensuse.org/repositories/games/openSUSE_11.3/
```[/URL]Click "Edit".

Edit that line and  change it to:

[URL="http://download.opensuse.org/repositories/games/openSUSE_12.1/"]```
http://download.opensuse.org/repositories/games/openSUSE_12.1/
```[/URL]

I confirmed that the URL exists.

Also change the sction of the Repostory Name from 11.3 to 12.1.

Refresh your repos.  You'll probably be asked to Trust the GPG key on that repo.  Go ahead and accept that.
It worked. :D It now says all packages are up to date, does that mean I am fine? :)

---

### Post by QIII on 2012-04-20
I'd say you are good.

Glad it worked out!

---

### Post by aligator12 on 2012-04-22
> **QIII said:**
> I'd say you are good.

Glad it worked out!
Thanks! I can't thank you enough! :D

---

