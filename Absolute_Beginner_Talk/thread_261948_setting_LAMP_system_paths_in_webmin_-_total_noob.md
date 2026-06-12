---
title: "setting LAMP system paths in webmin - total noob"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by studioq on 2006-09-20
I guess I should feel lucky. The system installed without a hitch. It boots, runs and shows up on the net. I am still learning quite a few things by reading, but this is where I could really use some guidance.

I have installed webmin (1.300.tar.gz) because without it I would be totally lost. The only problem seems to be that many of the paths set in the configuration of webmin lead nowhere. In the server section, no matter what I click on, the program tells me it isn't installed or isnt configured correctly. It did manage to locate Apache and MySql, but SSH - SSL -and many other just come up blank. I must admit I dont know enough about the system to figure out what the paths areto all the different devices.

I just dont know where to start looking. Is the problem with Dapper - is it with webmin? (Is it with me?)
Where do I begin to check to solve the issues?

I guess my other question would be: What parts of the LAMP install that are mentioned in the Webmin console are not "out of the box" with Ubuntu Server so to speak.

Thank you.
StudioQ

---

### Post by YeahBuntu on 2006-09-20
Hey I am setting up the same thing myself.

What exactly are you trying to configure.

I am a total noob too but I learned pretty early on how to navigate around the filesystem and use the (search) tool to locate a file I know has to be somewhere.

Anyway if you be more specific maybe I can help.  You are a bit further along with it than I am because I am currently just setting it up locally so I can try to " harden " it up before I open my router.

cheers!

noobs helpin noobs

---

### Post by studioq on 2006-09-21
The install is on an old i386 box with a p-III 733 and 256 of pc100 memory in it. I completely wiped the hard drives and went with a clean Ubuntu install. All of that went fine and so far I dont have any procbem with how the system works.

My real issue is with Webmin. When you go into the "module configuration" it gives you the ability to point the program toward the correct file paths. Either the program is broken or It installed with the wrong file paths by default and Now I must reset them. Without knowing how too figure our what the paths are to the installed servers such as SSH and SSL I am a little lost.

---

### Post by YeahBuntu on 2006-09-22
Hi again..

Ok so I went and logged into my webmin to see what you are talking about.  I see SSH Server under the "Servers" tab on the webmin interface ... when I click it.. I get the same thing you are.. so .. I start searching for the files 

Places---SEARCH FOR FILES

I choose file system where it says "LOOK IN FOLDER"

I then look for the first file that it wants the path for:  sshd 

This brings up plenty of locations for this 'file' 

Problem is I dont believe that any of those locations are what I am looking for so I choose to search for a more specific file in the configureator

So I search for "sshd_config" instead.

This turns up zero

which tells me I probably do not have SSH installed

so I fire up Synaptic Package Manager and look around for ssh  I am not going to install SSH yet but it is there for you to install .. after you install it you should be able to locate the 'files' and it may already be configured after you install it.

Hope I am right here since im a noob still myself 

anyone else care to give a yay or nay to what I say?

---

### Post by chrisfay on 2006-09-22
> which tells me I probably do not have SSH installed

Yes, you are correct. Webmin will give you an error related to the config file either being incorrect or the module not installed. You obviously need to have the software installed for webmin to administer it. 

Either search in synaptic for it, or you can look up the package at packages.ubuntu.com and install it using the CLI with apt-get or aptitude. 

Webmin is pretty good about using the correct default file locations for program/config files. Some new software will have new file locations that you have to adjust Webmin to, but for the most part, its almost always as simple as install the package and go. I know for a fact that SSH is.

Ex. Apache2 is one that you have to adjust the Webmin module to use or it defaults to editing Apache1 file locations.

---

