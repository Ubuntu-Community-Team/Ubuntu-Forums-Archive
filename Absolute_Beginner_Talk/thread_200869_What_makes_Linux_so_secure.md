---
title: "What makes Linux so secure?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by fridayxiii on 2006-06-20
I know that one reason many Linux users switch from Windows is the security factor.  Linux is advertised as being less vulnerable to spyware, malware, viruses, and hacker intrusions.  One thread I read before even installing Ubuntu said that Linux can be run in a personal environment w/out a firewall, anti-virus, or spyware hunter.  

I'm just wondering what is it about Linux that makes it so secure?  I did a bit of Googling but found most articles addressed the question from an enterprise web-server perspective.  I'm looking at the question more from the home user/home network side.  In addition, if I end up enabling my home wireless network w/my Win98 machine, are there security threats to my dual boot box to consider?  

Thanks for enlightening someone thoroughly enjoying their first cup of Ubuntu.  :grin:

---

### Post by aysiu on 2006-06-20
These things make desktop Linux more secure:

1. **Smaller target**. Why wreak havoc on a small percentage of users when you can do the same for the vast majority of users?

2. **Savvy population**. Why wreak havoc on generally computer-savvy users when you can wreak havoc on dumb users? There's a higher percentage of people who use Windows who will click on anything and give away their passwords for anything than there is for people who use Linux.

3. **Better default security model**: The first user (with the exception of Linspire) is a regular user, not the administrator. It's easy to set up a model (and Ubuntu has this out of the box) whereby you can temporarily gain administrator privileges to perform a particular task. Windows XP's "run as" function is crippled. Windows is built to be run as administrator. This may change with Vista. Who knows?

Any file needs to be made executable before it can be executed or run.

There are probably more answers, but those are the basic 3. I'd say #2 is the best reason. If you get more dumb users using Ubuntu, it won't matter how good the security model is.

---

### Post by siccness on 2006-06-20
I'd say another reason would be permissions in relation to user, group, other.

---

### Post by fritz_monroe on 2006-06-20
This is my understanding of it and my opinions.

If you were to somehow get a piece of malware on your Linux machine, the only parts of the system that the bad guy can mess with is the environment for the current user.  As long as you aren't running as root, they can do no permanent damage to the system.  Worse case, you go back in as root, delete the hacked account and create yourself a new account.

On Windows, this same attack can take over the entire machine because the first user account has admin permissions of the entire system.  Take over the account and you have the system.

And don't discount the smaller target that Linux presents.  If I was looking at doing the most damage, I'd attack the target with the most users.

Lets not forget that the average Linux user is much more computer saavy than the average Windows user.  Because of this, they are less likely to do something that would put them in danger, like launching an app that was sent to them by someone they don't know.

Lastly, let's not forget that Microsoft has made many enemies in it's rise to power.

---

### Post by rai4shu2 on 2006-06-20
1) Vulnerabilities cannot be hidden in open source programs.
2) Malware cannot be smuggled into a trusted repo.
3) Good (long) passwords can keep you safe from lazy hackers.

---

### Post by Nikusan on 2006-06-20
No services listening on any interface except loopback, so there's no need for a firewall.

---

### Post by IYY on 2006-06-21
Viruses and hacks are technically possible (though they pretty much don't exist for Linux today), but spyware is very unlikely. Most of the spyware problems in Windows come from security holes, mainly in Internet Explorer.

---

### Post by Fred Doolie on 2006-06-21
[QUOTE=aysiu]Any file needs to be made executable before it can be executed or run.[/QUOTE]

Meaning that if something evil got accdentally downloaded it couldn't be run unless you specifically made it runnable? What if there was something in the webpage code (Java, javascript or activeX) that made the file runnable on your system? Java and javascript are pretty powerful.

---

### Post by aysiu on 2006-06-21
Good point, Fred. In fact, almost all of Firefox's exploits are Javascript random runnings of code or escalations of privilege.

---

### Post by alaaji on 2006-06-21
[QUOTE=aysiu]Good point, Fred. In fact, almost all of Firefox's exploits are Javascript random runnings of code or escalations of privilege.[/QUOTE]

Which is why I run Firefox with the extension NoScript.  It turns off java and javascript for all websites except the ones that you specify.  Makes it a lot easier to surf the web that way IMHO.

---

### Post by aysiu on 2006-06-21
[QUOTE=alaaji]Which is why I run Firefox with the extension NoScript.  It turns off java and javascript for all websites except the ones that you specify.  Makes it a lot easier to surf the web that way IMHO.[/QUOTE]
NoScript is one of my favorite extensions.

---

### Post by Drakkor on 2006-06-21
aysiu, I have downloaded the NoSpript extension, could you tell me basically how it works, will a box pop-up asking my permission to run script from their site? Oops, nevermind, I see the options in the right hand section of the status bar. Thanks for the tip !

---

### Post by aysiu on 2006-06-21
[QUOTE=Drakkor]aysiu, I have downloaded the NoSpript extension, could you tell me basically how it works, will a box pop-up asking my permission to run script from their site?  Thanks ![/QUOTE] Basically, NoScript assumes that you want every site with Javascript (and Flash, too, if you enable that option) turned off.

One by one, you can "whitelist" certain sites to say, "Yes, allow Javascript and Flash on this site." You can also temporarily allow Javascript on a certain page.

Click on the *S* icon in the status bar, and you'll see all your options.

---

### Post by Drakkor on 2006-06-21
I see, very nice ! Thanks for the tip !!  Edit: and alaaji too,lol.

---

### Post by Drakkor on 2006-06-21
Momentarily,lol :-) ,and first off,there was a big Anti-Virus download, and then I had to re-boot the computer. Well I got to feeling very unsafe at that point and immediatlely re-booted to Ubuntu,lol.... :mrgreen:

---

### Post by MaximB on 2006-06-21
another few reasons I thought about are
1. there are hundreds of linux distributions on the web and it's very hard to "much" theme all with one virus
2. most of the virus "writers" are a linux users (most likly want's to get even with bill gates) so they won't harm there software
3. there are TONS of bugs in MS products - they will never fix them all
(I'm already imaganing blue 3d screen on vista)

---

### Post by Kilz on 2006-06-21
[QUOTE=MAXDDARK]
(I'm already imaganing blue 3d screen on vista)[/QUOTE]
ROTHLMAO I wonder if the blue screen will be transparent?  :D

---

### Post by Lord Illidan on 2006-06-21
Also consider this.

If Linux becomes more popular, sure, virus writers will become more focused on it. However, there will also be more developers looking for loopholes and vulnerabilities in the code. Which ensures that it maintains its security.


And Linspire, although it may run as root, is famous for having no services connecting to the internet, except http, I believe. So it is quite secure from internet access.

---

### Post by neoflight on 2006-06-21
my understanding is :

when u install an application it doesnt touch the kernel or system files...
it gets written to common folders to be listed in PATH...so that the application an be invoked easily....

i have observed in windows certain files that are specific to an installed program saved along with system files and such (for eg., dll files...)apart from IE vulnerabilities this might add to the overall system security properties..

and almost all installed programs can write into the windows registry...that goes with the permission characteristics....

please correct me if  iam wrong..

---

### Post by Drakkor on 2006-06-21
Just in case my Ubuntu goes belly up, I have just made a backup image of the whole deal,with Acronis True Image. Admittedly,you must use windows to accomplish this, but now after a week with Ubuntu I rarely have the need or
want to even get into windows,and when I do, I lock off the internet (too dangerous) and play some games or quick tasks,then back to Ubuntu I go !

---

### Post by Brunellus on 2006-06-21
[QUOTE=Lord Illidan]Also consider this.

If Linux becomes more popular, sure, virus writers will become more focused on it. However, there will also be more developers looking for loopholes and vulnerabilities in the code. Which ensures that it maintains its security.


And Linspire, although it may run as root, is famous for having no services connecting to the internet, except http, I believe. So it is quite secure from internet access.[/QUOTE]
...a security that is all too tenuous, as the sort of user who would run Linspire is likely also the sort of user that will click "anything".

Once they execute somethign with root privileges, well......

---

### Post by mdsmedia on 2006-06-21
Apart from the "security by design" where the first and regular user doesn't have admin priveleges by default, the fact that no services are left open by default, the sheer number of different distributions....making it difficult to zero in on one system, and making the target even smaller....., the repositories was mentioned, but not given enough emphasis or explanation.

Usually when installing software you will install it from repositories of known applications which, as previously was mentioned, have had the attention of many experienced users/developers and being open source the code is available for all to see and therefore difficult to hide malware within. As long as you use programs available in OFFICIAL repositories there is little likelihood of malware within the application.

Another point is that any flaws in the OS are usually picked up on a timely basis by developers and fixed on a timely basis in regular updates.

Which leads to the "savvy users" reason. If you don't download software from sites other than the repositories you have very little chance of receiving malware in software downloads. Free, regular updates will protect your system from flaws already found. Having espoused the repositories, if you download from other sources this doesn't open up your system to malware, if you are sensible about where you download from and what you download.

If you receive something from an outside source, through, say, email, it is difficult for it to grab a hold on your system because YOU have to make it executable, usually by using SUDO or ROOT. While not impossible, this is another barrier to malware.

---

### Post by shanepardue on 2006-06-21
*if I end up enabling my home wireless network w/my Win98 machine, are there security threats to my dual boot box to consider?*

i wouldn't recommend using windows 98 as micro$oft has recently stopped supporting it and it's wide open to be exploited.

---

### Post by heroticpaladin on 2006-06-21
[QUOTE=fritz_monroe]
If you were to somehow get a piece of malware on your Linux machine, [COLOR="Red"]**the only parts of the system that the bad guy can mess with is the environment for the current user.**[/COLOR]  As long as you aren't running as root, they can do no permanent damage to the system.  Worse case, you go back in as root, delete the hacked account and create yourself a new account.
[/QUOTE]

Hello All.

I am a complete linux newbee, not even a week ... :roll: 
And I deleted my win xp partition!! =D> 

I loved Ubuntu, and beside setting up the Nvidia drivers, I had no troubles.
I am even considering to upgrade the standard kernel from instalation to enjoy my PentiumIV.

Anyway.

I only have 2 partitions on my laptop.
-1- Ubuntu
-2- Swap

As the only part of the system that can be damaged is the current user, would it be possible and interesting to dedicate a specific user-account just for the data?

Lets say I create the user-account "data" and I put all the pictures, mp3s, divx, etc., in it. But I only use my regular user-account to use the pc.

If I have a pb, I delete the regular user-account, and create a new one.
This way I don't loose any data.

Cheers.

---

### Post by bruce89 on 2006-06-21
[QUOTE=Nikusan]No services listening on any interface except loopback, so there's no need for a firewall.[/QUOTE]
Not to mention there is no NetBIOS running as default.
[QUOTE=MAXDDARK](I'm already imaganing blue 3d screen on vista)[/QUOTE]
I believe the BSOD is to be recoloured red.

---

