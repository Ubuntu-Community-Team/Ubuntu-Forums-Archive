---
title: "directory permission confusion"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by mistux on 2008-03-10
I am having trouble with the access rights to /var/www and don't understand why.

I am new to Ubuntu (and Linux) but not to Windows.  I instaleld Ubuntu 7--Feisty Fawn and then used the get-apt to download and install Apachi, MySQL and PHP5.  

Then I did the same with Gallery (a photo site), although it did not get the latest version of Gallery2 for some reason.

I noticed that Apachi created some htm files in the /var/www directory and when I go to another PC on my local network I can etner the IP adress and see the html page saying "It works"  

So far so good, but I need Gallery to be in that directory as well (I think) and I can't copy and paste it into there, I can't even create any documents in that directory for that matter.  So, I went and did a chown and made me the owner and then copied over the Gallery2 files (that I downloaded from their site and unzipped) but now I can't use the IP address to get to it like before so I can't run the instlal program.

I am thinking that Apachie and or PHP can't "access" the /var/www directory sufficiently to do what it needs to do.  But I don't know what or who to give rights to that directory now.

I am confused about the whole process, but more then willing to work through it.  I had my photo site up and running on a Windows box but it just died and I thought that I would try Ubunto but my knowlwdge is that of a beginner.

Any help would be appreciated.

Thanks, Mitch

---

### Post by alenis on 2008-03-10
I think that. for apache to work, the /var/www and its subdirectories must be owned by root. So chown them back to root and everything should work. If you need to copy other files into /var/www use sudo.

---

### Post by mistux on 2008-03-10
How do I use the sudo to copy files into that?

---

### Post by mistux on 2008-03-10
> **alenis said:**
> I think that. for apache to work, the /var/www and its subdirectories must be owned by root. So chown them back to root and everything should work. If you need to copy other files into /var/www use sudo.


When I did a
```
chown -R root /var/www
```

It said "Opperation Not Permitted"  on every line, so it did not work.  Did I do somethign wrong?

---

### Post by theinnercityhippy on 2008-03-10
Hello there

I'm not an expert but I've had a bit of experience with changing permissions so I'll try my best to help you out.

First cd to the directory you want

# cd /
# cd var

then change the permissions so that all users can access it

 # sudo chmod 777 www

This will ask you for your administrator password, enter it and you will have set its permissions so that all users can use it.

also you can change the permission recursively by adding the -r flag like so:

# sudo chmod 777 -r www

Hope this helps :-)

-Jimdog-

---

### Post by alenis on 2008-03-10
If you have already copied the file under /var/www and changed the permission, Apache should work fine.
If you wnat to copy files into /var/www you will have to prefix sudo to cp:
```
sudo cp file-to-be-copied /var/www
```

---

### Post by mistux on 2008-03-11
Thanks to all for your help.

I had to do the chmod 777 then the chown root then it worked!

It is unfortunate that I can't use the Ubuntu GUI to drag and drop files into that directory like I could in Windows, but I guess I will just have to learn the command line commands to do things in that directory.

Thanks again for your help.  

How do I give you "thanks?"  --->Oh, Just found the little icon.

---

### Post by alenis on 2008-03-12
Typing 

```
gksudo nautilus
```

in a terminal window will open nautilus with superuser rights. You will be able to move files all around in a GUI without any problem. However, using nautilus this way could be dangerous: you could accidentally delete or alter files in important system area causing your system not to work properly anymore.

---

### Post by scorp123 on 2008-03-12
> **theinnercityhippy said:**
>  then change the permissions so that all users can access it 

 # sudo chmod 777 www

This will ask you for your administrator password, enter it and you will have set its permissions so that all users can use it.

also you can change the permission recursively by adding the -r flag like so:

# sudo chmod 777 -r www  Hey sweeeeeet !!!! **A web server with world-writable permissions !!!!! ** :twisted:

Can you please tell us which web servers you have configured so far? With those file permissions the possibilities are endless :twisted:  ...

**[COLOR="Red"]Seriously:[/COLOR]** "chmod 777 /var/www"  <== **[COLOR="Red"]That was bad advice![/COLOR]**  That web server is now open for hacking.

---

### Post by bodhi.zazen on 2008-03-12
> **theinnercityhippy said:**
> Hello there

I'm not an expert but I've had a bit of experience with changing permissions so I'll try my best to help you out.

First cd to the directory you want

# cd /
# cd var

then change the permissions so that all users can access it

 # sudo chmod 777 www

This will ask you for your administrator password, enter it and you will have set its permissions so that all users can use it.

also you can change the permission recursively by adding the -r flag like so:

# sudo chmod 777 -r www

Hope this helps :-)

-Jimdog-

> **mistux said:**
> Thanks to all for your help.

I had to do the chmod 777 then the chown root then it worked!

It is unfortunate that I can't use the Ubuntu GUI to drag and drop files into that directory like I could in Windows, but I guess I will just have to learn the command line commands to do things in that directory.

Thanks again for your help.  

How do I give you "thanks?"  --->Oh, Just found the little icon.

Changing the ownership / permissions of system files (anything outside of your /home) is a fast way to getting cracked or having to re-install the OS.

You can use sudo from the command line ```
sudo -i
```to become root.

If you want a graphical program with root access use gksu (kdesu with kde)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I have seen many people needing to re-install after changing ownership / permissions outside of /home.

---

### Post by scorp123 on 2008-03-12
> **mistux said:**
>  I had to do the chmod 777 then the chown root then it worked! **That was bad advice. [COLOR="Red"]Seriously![/COLOR] **Your web server is now open for hacking thanks to those permissions.

I'd strongly suggest you follow the advice given to you by **alenis** a little further up ... That would be the proper way to do it without endangering your installation.

---

### Post by Oldsoldier2003 on 2008-03-12
The best way to handle the whole situation is to create a site in a users space then edit /etc/apache2/sites-available/default

then of course /etc/init.d/apache2 restart

---

### Post by mistux on 2008-03-13
> **scorp123 said:**
> Hey sweeeeeet !!!! **A web server with world-writable permissions !!!!! ** :twisted:

Can you please tell us which web servers you have configured so far? With those file permissions the possibilities are endless :twisted:  ...

**[COLOR="Red"]Seriously:[/COLOR]** "chmod 777 /var/www"  <== **[COLOR="Red"]That was bad advice![/COLOR]**  That web server is now open for hacking.

:!: 
[COLOR="Red"][SIZE="4"]What should they be for /var/www then so I can make sure to put them back on mine!!![/SIZE][/COLOR]
:!:

---

### Post by fmartinez on 2008-03-13
> **mistux said:**
> :!: 
[COLOR="Red"][SIZE="4"]What should they be for /var/www then so I can make sure to put them back on mine!!![/SIZE][/COLOR]
:!:

/var/www is just a default.... you can put your web files on any directory and have a virtual host point to that directory. that would be the best way to go. 
And you set those permissions to what ever you want.

---

### Post by Oldsoldier2003 on 2008-03-13
> **mistux said:**
> :!: 
[COLOR="Red"][SIZE="4"]What should they be for /var/www then so I can make sure to put them back on mine!!![/SIZE][/COLOR]
:!:

rwxr-xr-x

---

### Post by handydan918 on 2008-03-13
> **Oldsoldier2003 said:**
> rwxr-xr-x

That would be 755, numerically.

---

### Post by mistux on 2008-03-13
> **handydan918 said:**
> That would be 755, numerically.

Thanks, I needed the numerical value,

---

