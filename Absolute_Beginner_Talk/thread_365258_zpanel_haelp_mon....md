---
title: "zpanel haelp mon..."
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by hockey97 on 2007-02-19
How to unzip .zip files in ubuntu 6.10 server?? I am trying to install zpanel to my server, and I know the wget command and done it I download it to my server but now how to unzip  a .zip file , I tried the command unzip then file name and said cannot find command, then I did man unzip same error, then man zip nothing then I did man tar and gave me a manual  it did that to see if it's the server or whatever but shows that zip commands dont exist in my server.

Do I need to install a package that will install zip commands??? I been working on the server for about 2 months clsoe to 3 months and havent got it up and running.

---

### Post by solar george on 2007-02-19
```
sudo apt-get install unzip
```

Should install the unzip utility.

If you have ubuntu running on a desktop firefox includes an ubuntu package search tool in the search engines box. Try using this to find the tools that you need.

---

### Post by hockey97 on 2007-02-19
Hi thanks it works no but another problem I don't fully know how to install it, the files are unzipped and sitting on my server now how to install it and run the program, pluse I also unzip and install mozilla firefox, but I don't know what command to put in to run it??

any ideas?? Sorry for the noob questions but I don't know linux syntax I know dos and also alot of other programming langos.

---

### Post by solar george on 2007-02-19
If [this]("http://www.thezpanel.com/") is where you got the software from they have their own forums that will include people who have experience with the software.

I am downloading the software from their site an will see if I can work out what you need to do. 

In the meantime search the howto forum and the wiki for zpanel. 

If you find a howto could you post a link to it in this thread.

---

### Post by solar george on 2007-02-19
Try reading the readme.htm in the folder where Zpanel was extracted.

N.B. Most linux programs include a README or and INSTALL file that contain instructions for installing.

To install Firefox use a similar command to the one used to install unzip:

```
sudo apt-get install firefox
```


If you need to search for a program to install use
```
apt-cache search *programname*
```
This will give you a list of programs that are similar.

---

### Post by hockey97 on 2007-02-19
I will give it a try thanks  and I will post if I find any how to tutorials on here.

why are you installing it, if you don't mind me asking??? if it's becuse of me you don't really need too.
I installed firefox using what you suggest that sudo aptitude install mozilla-thunderbird and it download it and installed it I read the man of firefox and it said in order to run it to put firefox as the command so I did and it gave me an error it said connot be diplayed gts 980 error. is it supposed to be a graphical browser or is it a text type browser??

I can't fully understand why I got the error sorry for not being much help or anything but I am used to windows and this is the first time using linux type oses. or servers ect.

---

### Post by n8bounds on 2007-02-19
um...if you installed just the server edition and never installed ubuntu-desktop or any other xserver & window manager, firefox has nothing To Run In, per say...knowhatimean?

---

### Post by hockey97 on 2007-02-20
your joking?? so this means I have to repartition and  install the os one of ubuntu??

well I have xp pro,  is their a way that I can just run ubuntu6.10 server while I am on xp pro?? and use a the internet interfaces to upload my stuff in the server ?? 
I am a noob to linux I alway's wanted to get into it a long time ago and so lately I decided when I want a server and make my own pro hosting stuff like hosting my websites with my own stuff domain names but I don't like having half control over my server like someone said I need to register my domain name with my isp and I don't like that idea I check it out and found out it's 50 bucks for a custome domain name meaning www. somthing.com and 30 for subdomain like [www.isp/yourstuff.com](www.isp/yourstuff.com)  ect.

I don't think I would need firefox but I just thought that if I could run it on ubuntu 6.10 it would help for me to test my websites and look at them to see if it's all good.

but is zpanel a graphical interace on ubuntu 6.10?? like  if I run zpanel in ubunutu 6.10 I should get a graphical menu or do I do this through the internet?? becuse I unzip it and found alot of .php files and I am not sure?? 
I am more of a graphic type user but console screen I don't mind it but if I knew what commands do what and how to config the server to do what I want to do would then be much better.

---

### Post by solar george on 2007-02-20
> why are you installing it, if you don't mind me asking?
New open source software that I hadn't come across before - and if it's any good it'll help on my test server.

> so this means I have to repartition and install the os one of ubuntu??

No, just run 
```
sudo apt-get install ubuntu-desktop
```

This will download and install the full ubuntu desktop - including firefox.

---

### Post by solar george on 2007-02-20
> I check it out and found out it's 50 bucks for a custome domain name meaning www. somthing.com and 30 for subdomain like [www.isp/yourstuff.com](www.isp/yourstuff.com) ect.


Yes you don need to register with a company because they have access to the registrars for the domains. Search around more $30 for a sub domain sounds far too much.

Once you have registered a domain you can redirect it to you computer from the isp's controll panel.

---

### Post by hockey97 on 2007-02-20
So their is no way around the isp's?? what if I find some way to get to the registar's, 

I always' waoundered how aol and all the internet providers actualy provide you with internet access??  I heard they make contracts with ameriatech or  the company thta lay's out the lines ect and also pay the person who made the internet and also hear their is a internet 2 coming out but I don't know what's the difference between internet and internet2?? I hear it's about speed and graphicas using fiberoptics to connectect the world??

Thanks I will run that destop thing.

The reason I am trying to find a way around isp's becuse I want full control on the service I provide I would really hate if my isp screw up or  if they got bribed money to shut me down or if the gov want's me to be shutdown becue of violation but then later on find out it was a mistake and not me but anothers persons computer ect thses things make a huge effect on home much you can make having an internet service meaning a website ect. 
But I have seen alot of services with high rates I don't see good cheap prices for hosting my domain. I also heard their is a law for U.S citizens that you can only pick hosting services in the U.S becuse they want all U.S websites to be monitored some new bill on the floor I read that stat's that the isp are responsible to keep a log of their customers activites this is for like aol ect those internet providers if they don't they can face fed charges.

I just installed the desktop part works good but no audio,  and I tried installing zpanel in the desktop and failded, still trying to install the panel thing.

with using the desktop will I still be able to config and look into mysql databases and other stuff like ftp?? how could I host games??

---

### Post by hockey97 on 2007-03-06
Hi I have a problem I don't know how to add files ect into a mysql database, in commmand promt ect, does anyone knoe how to?? I am trying to put zpanel and also phpadmin in it.

---

### Post by hockey97 on 2007-03-06
Also Is their any way I can run windows xp and us xp pro while ubuntu 6.10 is running in the backround?? I looked at mv server and to me look's like another servee, I just need somthing so that when I am in windows I can turn on and run my ubuntu 6.10 to let it run in the backround while I am still on windows xp pro, I use windows for everyday stuff and ubuntu 6.10 as a server but I don't want to use it as a everyday os I use windows xp pro, so I want ubutu to still be on and running so I can in windows xp can look on the internet ect and see my server up and running, this would be the same computer I have 2 hard drives one with windows xp pro and the other ubuntu 6.10. 

Any ideas on how to do this?? I basicly want ubutuntu to be running while I have xp pro running, I want the main os  windows xp pro to be diplayed, I want ubuntu but be in the backround running not showing anything .

is that possible?? need help with how to do this. I don't want to have to be in ubuntu 6.10 to have the server or my websites to have them running I want to be in xp pro and have ubuntu running so I can see my websites on the internet while I am in xp pro.

Thanks for your time.

---

### Post by hockey97 on 2007-03-18
Hi I need to know how to uninstall mysql. becuse I get an error when I open php files that the error say's that mysql extension failed to load. 
Any ideas would help.
Thanks for your time.

---

