---
title: "How do i download automatix"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by manojvekaria on 2006-09-05
I'm completely a newbie!

i got a very slow connection at m house.
but got a fast one at uni.

how do i download the automatix.deb from the web, and store it on my 1 gig flash.

It would be a great help.
I tried some links, but the sites say, the links have been removed!!!

](*,) ](*,) 
____________
[SIZE="1"][/SIZE]Automatix, do things magixally!!

---

### Post by Fedz on 2006-09-05
[The Home of Automatix](http://www.getautomatix.com).

Command
wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
chmod 755 ~/automatix-installer
./automatix-installer

Hope this helps.

---

### Post by manojvekaria on 2006-09-05
My uni computers run on windows. I want to download the .deb file of automatix, which has all the applications on it.

How do i do that, Any one got a idea;)

---

### Post by xyz on 2006-09-05
Hi manojvekaria,
I don't know but Automatix has a forum where you might find out about this or post your question.
[http://www.getautomatix.com/forum/index.php?showforum=15](http://www.getautomatix.com/forum/index.php?showforum=15)
How slow it your connection? Wouldn't it be worth it anyways?

---

### Post by omns on 2006-09-05
.

---

### Post by wpshooter on 2006-09-05
My recommendation would be that you NOT use Automatix.

Install any programs you need thru Synaptic function of Ubuntu or download and install them directly from the application programs vendor site.

Good luck.

---

### Post by Klaidas on 2006-09-05
I agree with that.
Automatix might be more simple right now, but if you won't be able to install apps suing a few terminal commands/synaptic, it mean you didn't really learn "leenooks"

---

### Post by Naegling23 on 2006-09-05
Im gonna disagree, install and run automatix.  There are plenty of other opportunities to learn how to install the software manually.  If you run automatix, linux can compete with windows.  If you dont, you will be pulling your hair out trying just to play music.  Im a recent linux convert, and if it wasnt for automatix, I would still be using windows.

---

### Post by xyz on 2006-09-05
I agree in a way but back when I knew absolutely nothing about Ubuntu, (and I don't know much right now) Automatix helped! Automatix works and when nothing works because I didn't know how, it's important and it gave courage to go on.

I like to learn so Automatix didn't prevent me from finding out more and/or other ways to install stuff. Someone who likes and needs to learn, find out about stuff will do so, Automatix or no Automatix.

People who aren't interested in finding out (perhaps because they simply don't have time to do so), will go back to Windows.

---

### Post by wpshooter on 2006-09-05
One other reason I suggest not using Automatix is that in my experience it does not do a 100% job of installing some of the software that it is supposed to.  When you get finished some of the functions you were wanting still do not work like they are supposed to and you a stuck trying to find out what the problem is and how to fix it.

---

### Post by xyz on 2006-09-05
I'm sure you're right, wpshooper; however I never encountered pbms that you describe. Maybe I got lucky and never needed to install problematic software via Automatix!! Besides you can always totally remove Automatix or only THE soft that's causing problems and then go Restricted Format.

Back under Breezy, a member by the name of Patrick wrote a great and very interesting script about that. No idea if he kept it up-to-date? 

I think, in my humble opinion, that all the suggestions on this thread are good and can help **manojvekaria** whose initial question was:

> how do i download the automatix.deb from the web, and store it on my 1 gig flash?

---

### Post by wpshooter on 2006-09-05
I don't believe that the author of Automatix has designed it to work that way or at least not at this point in time.

I still suggest the inquirer is probably better off not using it, period.

---

### Post by omns on 2006-09-05
.

---

### Post by wpshooter on 2006-09-05
Well, I think it gives them a pre-warning as to what they might expect.

The ultimate decision as to wheather they try it, is, of course, up to them.

I don't have time to describe in detail every thing that I find wrong with all of the software that is available for possible use.  But I assure you that I don't warn people about possibly considering not using software that I think will reliably perform the tasks that it is designed to do.

I will gladly test Ubuntu's beta releases and report any bugs that I come across, but every auxiliary type software that is available for possible use.

---

### Post by omns on 2006-09-05
.

---

### Post by Sweet Spot on 2006-09-05
As a very recent Windows convert myself, I'm going to have to give my praises to Automatix. Some of us don't have the necessary time to spend trying to figure out how to configure the many things which are required to run the types of programs we're used to. Beyond programs, I was searching and found just tons of conflicting (or just old and redundant) information about how to "properly" install the proprietary Nvidia drivers. Automatix gave me the will to continue on and actually WANT to learn about the things that Automatix did for me. 

And one day, I swear I will, but right now, I'm far too busy to even think about it. Ubuntu has been hailed as one of the upcoming desktops to compete with Windows eventually, and so I think that it's only fair/natural, that anything which can be done to make its operations easier, should be done. The type of features which Automatix offers, should IMO be an inherant trait of Ubuntu in general. I mean, tinkering is good, it's great but, so is just being able to install an OS and getting to use its features right away. 

Linux will always have its severely geek driven population, that won't change, but what's wrong with having at least ONE distro, which people who aren't total geeks can attach themselves to ? The bigger picture there is that people whom aren't geeks, might actually find themselves exploring the deeper sides of Linux, but to be honest, if regular people are turned off by a distro because they can't even get simple things done, how could you blame them for not wanting to deviate from their norm ?

Yes, there will be a group of people who will be lazy and just take all the easy rides they can get, which I think is fine too, because you have to cover all bases. But if there's always this high and mighty attitude coming from Linux geeks who seem to not even want a distro like Ubuntu to become successful because it will endanger their way of geek life, then I'm afraid that this self serving way will only keep Linux behind the major OS distributors (Mac, Win) and IMO, that can't be good for anybody. 

Everything, should be Automatix ! 

Doug

---

### Post by devilsadvocate1987 on 2006-09-05
Well, in response to the original question, I think there is no point in you downloading automatix at your univ. Automatix itself is a tiny application -  a script with a gui. When you run automatix it gets the packages from the internet. So, you'll be getting a ~1MB package over the fast connection at your univ, and using your slow home connection to get the ~100 or 200 mb of packages (of course, depending on what you select that can be much smaller or a little larger). 

If you still want to do that, though, the 'wget' command is basically one that downloads a file. Use the link that you're supposed to use with wget on any browser you want and download the file that the link points to. Then, copy that file to your linux computer and run the other commands.

---

### Post by wpshooter on 2006-09-06
> **Sweet Spot said:**
> As a very recent Windows convert myself, I'm going to have to give my praises to Automatix. Some of us don't have the necessary time to spend trying to figure out how to configure the many things which are required to run the types of programs we're used to. Beyond programs, I was searching and found just tons of conflicting (or just old and redundant) information about how to "properly" install the proprietary Nvidia drivers. Automatix gave me the will to continue on and actually WANT to learn about the things that Automatix did for me. 

And one day, I swear I will, but right now, I'm far too busy to even think about it. Ubuntu has been hailed as one of the upcoming desktops to compete with Windows eventually, and so I think that it's only fair/natural, that anything which can be done to make its operations easier, should be done. The type of features which Automatix offers, should IMO be an inherant trait of Ubuntu in general. I mean, tinkering is good, it's great but, so is just being able to install an OS and getting to use its features right away. 

Linux will always have its severely geek driven population, that won't change, but what's wrong with having at least ONE distro, which people who aren't total geeks can attach themselves to ? The bigger picture there is that people whom aren't geeks, might actually find themselves exploring the deeper sides of Linux, but to be honest, if regular people are turned off by a distro because they can't even get simple things done, how could you blame them for not wanting to deviate from their norm ?

Yes, there will be a group of people who will be lazy and just take all the easy rides they can get, which I think is fine too, because you have to cover all bases. But if there's always this high and mighty attitude coming from Linux geeks who seem to not even want a distro like Ubuntu to become successful because it will endanger their way of geek life, then I'm afraid that this self serving way will only keep Linux behind the major OS distributors (Mac, Win) and IMO, that can't be good for anybody. 

Everything, should be Automatix ! 

Doug

I agree with some of what you say but if users continue to use Automatix and other third party add-ons, this **MAY** give less incentive for the developers of Ubuntu to incorporate these functions into the O/S itself.  Like you say, it would be nice if all of these functions were out-of-the-box.

---

### Post by manojvekaria on 2006-09-06
K guys got it. automatrix is like a script containing scripts which will install other programs.

So what i should do is that check the list of automatrix, and then download the .deb files of what i need.

Thanx guys. I thought automatrix was like a app, which contains all those programs ziped.

is my assumtioin right???](*,)

---

### Post by Sweet Spot on 2006-09-06
> **wpshooter said:**
> I agree with some of what you say but if users continue to use Automatix and other third party add-ons, this **MAY** give less incentive for the developers of Ubuntu to incorporate these functions into the O/S itself.  Like you say, it would be nice if all of these functions were out-of-the-box.

With all due respect, I'm going to have to disagree with you. I think this should actually give the devs MORE incentive to incorporate said features/functions, because it's been said that the Automatix script can often break someones configuration and mess up other things.  

And even though Automatix isnt' entirely given all thumbs up by the Ubuntu team, it's still supported by them, seeing as how there's no official word for it to not be developed. In fact, it's included IN the OS, so there's a bit of a contradictory information in regards to its status. 
Just to back that up: > 
                     Originally Posted by **whatrucrazy**                     [[IMG]http://www.ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://www.ubuntuforums.org/showthread.php?p=1465252#post1465252")                 
                 [I]o
And more to the point Automatix is not a part of any distro's main install...[/I]
                  Then from [[IMG]http://www.ubuntuforums.org/customavatars/avatar7727_2.gif[/IMG]]("http://www.ubuntuforums.org/member.php?u=7727") 			 			 				 					 					[mhancoc7]("http://www.ubuntuforums.org/member.php?u=7727") 					 :                
> Well, this simply isn't true. It is included in Ubuntu CE's main install. I think that is the reason for the whole discussion. The original poster does not agree that it should be included in Ubuntu CE. 

Just wanted to clear that up a little.

Jereme 
And if I'm correct, I doubt that the Ubuntu devs really want people using a script to install something which breaks their OS.

I think then, that they'll have to come to terms with a better solution, and give the people what they want, or else another distro will eventually catch up to where Ubuntu is now, and wind up surpassing Ubuntu in this respect.

---

### Post by omns on 2006-09-07
.

---

### Post by Sweet Spot on 2006-09-07
> Ubuntu CE and itchtux are not official projects of the Ubuntu community so it is incorrect that Automatix is included in the distro. It would be more accurate to say that Automatix is included in an unofficial offshoot of the distro.

I wasn't aware of that, and thus, stand corrected sir, thank you. 

>  Some may see it as a newbie tool but as a more experienced user I find it an invaluable time saver in setting up new machines. 
Pretty logical assertion. I've been throwing the words "Linux" and "Ubuntu" around to my friends lately, (a lot) and a couple of them (including a mac guy who actually works for Apple) have been inquiring back, about the possibility of running Ubuntu. If Automatix didn't exist, I'd probably be a lot more hesitant to (1) recommend it to them and (2) offer to set it up for them. 

With the exception of Wine, [to run DVD shrink] most other things work(ed) pretty much out of the box for me. Though I guess MMV for different hardware configs.

---

