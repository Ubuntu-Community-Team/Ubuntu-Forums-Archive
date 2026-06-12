---
title: "How to install a program"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Alien260 on 2006-07-18
hello, 

i just started using ubuntu from a few days, and i am enjoying the whole experience the only thing i cant really understand well (coming from a strong Windows background) is how to install programs. 

i did all the basic stuff like update the programs i went to 

**Applications - add/Remove **

i even went to the advance setting 

**System - Admin - Synaptic package manager **

the problem i have is when i have to install things manually, i have been reading about having to start the installers from the terminal????????

i ll give you a practical problem i have, i need to install flash player 7 for firefox i downloaded the files to my desktop, but then after that i cant open it with GDebi package installer (which is what i did to install skype) i can just extract the file (called install_flash_player_7_linux.tar.gz) using Ark. 

when i do this and click on the file installer i get a message that says "Do you want to run "flashplayer-installer", or display its contents?" i say run and nothing happens. 

can anyone help this poor noob :confused: 

thanks

---

### Post by briguy on 2006-07-18
You're on the right track with Synaptic - don't try to install the downloaded version.  Here are a couple of references:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

[https://help.ubuntu.com/community/Repositories/CommandLine?highlight=%28multiverse%29](https://help.ubuntu.com/community/Repositories/CommandLine?highlight=%28multiverse%29)

Understanding how repositories work is key - they are where programs "come from."  You'll have to enable the multiverse / universe repos.

---

### Post by lowey23 on 2006-07-18
Hi, Alien260, welcome

Have a look at this site (written by aysiu)

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

It has heaps and heaps of excellent, simple explanations and how-to's which you will find very useful. I certainly did (and still do)

Cheers

Lowey

---

### Post by Sef on 2006-07-18
Read this pictorial tutorial on how to [install anything.]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Alien260 on 2006-07-18
thanks all so much for answering back so quickly i will read all of the info you gave me and let you know.

thanks again

---

### Post by Sef on 2006-07-18
You're welcome.  Please post any other questions that you have.

---

### Post by Alien260 on 2006-07-18
hello, 
i have read over the links given to me twice now and i m trying to install flash on my machine manually but i have a problem when "compiling it" the info says i have to type "make" but when i do that i only get an error. 

this is what i m writing in the terminal:

alien@alien:~$ cd /home/alien/Desktop/install_flash_player_7_linux
alien@alien:~/Desktop/install_flash_player_7_linux$ ./configure
bash: ./configure: No such file or directory
alien@alien:~/Desktop/install_flash_player_7_linux$ make
bash: make: command not found

according to the link 
[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

it should compile the script but it dosnt?? :confused: 

can some one help 

thanks

---

### Post by PriceChild on 2006-07-18
You need to install the basic compiling tools:

sudo apt-get install build-essential

---

### Post by macgig on 2006-07-18
id say for me, not being able to install apps is the most frustrating part so far.... ](*,)

---

### Post by briguy on 2006-07-18
> **macgig said:**
> id say for me, not being able to install apps is the most frustrating part so far.... ](*,)

You're making things more difficult than they have to be :)

Try following these instructions - don't worry about compiling anything:
[http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

---

### Post by mostwanted on 2006-07-18
> **Alien260 said:**
> hello, 
i have read over the links given to me twice now and i m trying to install flash on my machine manually but i have a problem when "compiling it" the info says i have to type "make" but when i do that i only get an error. 

this is what i m writing in the terminal:

alien@alien:~$ cd /home/alien/Desktop/install_flash_player_7_linux
alien@alien:~/Desktop/install_flash_player_7_linux$ ./configure
bash: ./configure: No such file or directory
alien@alien:~/Desktop/install_flash_player_7_linux$ make
bash: make: command not found

according to the link 
[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

it should compile the script but it dosnt?? :confused: 

can some one help 

thanks

First of all, Flash 7 is in the repos, installing it manually is a waste of resources.

Second of all, not all tar.gz arhives are source packages. a tar.gz is like a zip (only not proprietary) so anything can be inside them. In the case of Flash, you have a closed-source program, so obviously they won't ship the source code in their tar.gz packages. Instead it should have some executable installer inside it that you need to run.

But as I said, it's in the repositories, you just need to enable the correct one. Read the guide in my sig (also posted by someone else earlier), the info you need is in the appendix section.

---

### Post by kdragon on 2006-07-18
> **briguy said:**
> You're making things more difficult than they have to be :)

Try following these instructions - don't worry about compiling anything:
[http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

thx u so much

---

### Post by Alien260 on 2006-07-19
> **kdragon said:**
> thx u so much

i tried writing that in the terminal but this is what came out 

alien@alien:~$ sudo apt-get install flashplayer-mozilla
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla


why did that come out the installer is sitting on my desktop?? 

thanks

---

### Post by Alien260 on 2006-07-19
> **briguy said:**
> You're making things more difficult than they have to be :)

Try following these instructions - don't worry about compiling anything:
[http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

i ment this ..

---

### Post by Christmas on 2006-07-19
Hi. To install the Flash Player plugin you have two options. Once you have your universe/multiverse activated in your repositories type in the Terminal:
```
sudo apt-get install flashplugin-nonfree
```
Or, extract the .tar.gz file and copy the libflashplayer.so and flashplayer.xpt file into Firefox's plugins directory.

---

### Post by Alien260 on 2006-07-20
> **Christmas said:**
> Hi. To install the Flash Player plugin you have two options. Once you have your universe/multiverse activated in your repositories type in the Terminal:
```
sudo apt-get install flashplugin-nonfree
```
Or, extract the .tar.gz file and copy the libflashplayer.so and flashplayer.xpt file into Firefox's plugins directory.

i think i m doing something wrong because i always get the same error, i have all the multiverse activated and i still get this message 

alien@alien:~$ sudo apt-get install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfr

thanks

---

### Post by Lord Illidan on 2006-07-20
Can you hand us your /etc/apt/sources.list please? Copy it here.

---

### Post by Alien260 on 2006-07-20
hello, 

i managed to fix it i installed automatix and got it with the rest of the apps. 

thanks for the help everyone

---

