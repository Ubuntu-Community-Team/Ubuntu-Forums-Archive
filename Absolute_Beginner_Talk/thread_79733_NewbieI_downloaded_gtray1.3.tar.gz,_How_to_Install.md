---
title: "Newbie:I downloaded gtray1.3.tar.gz, How to Install it ?"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-20
after untaring the  gtray.tar.gz

 I installed these packages ... 

    ruby libopenssl-ruby libgconf2-ruby libgtk2-ruby libgtk-trayicon-ruby

then, what should I do now plz ?

thanks

Pat'

---

### Post by aysiu on 2005-10-20
There's no readme file in the extracted .tar.gz?

---

### Post by patrick295767 on 2005-10-21
[QUOTE=aysiu]There's no readme file in the extracted .tar.gz?[/QUOTE]


  This is a small notification area applet to check your GMail account
  and notify you when you have new email. It is written in Ruby
  (see [http://www.ruby-lang.org/](http://www.ruby-lang.org/))
  
  To use this, you need:

    * Ruby
    * The openssl bindings for ruby (for [https://)](https://))
    * Gtk+ 2.0, GConf 2
    * The Ruby bindings for gtk and gconf
    * The gtktrayicon library

  The first two of these are found in the standard Ruby distribution
  ([http://www.ruby-lang.org/)](http://www.ruby-lang.org/)).  The remaining three are found in the 
  ruby-gnome project ([http://ruby-gnome2.sourceforge.jp/)](http://ruby-gnome2.sourceforge.jp/)).
    
  If you run debian, you need to install these packages:
  
    ruby libopenssl-ruby libgconf2-ruby libgtk2-ruby libgtk-trayicon-ruby

  You can run gtray multiple times to monitor different accounts. This
  must be specified on the command line with a profile name, for example:

    $ gtray                      # use default profile
    $ gtray shoe                 # use the profile named "shoe"

  I am not an employee of google. This program is not endorsed by
  google. Do not send them emails about it. Google and their logos
  are registered trademarks.

---

### Post by patrick295767 on 2005-10-21
I have found a workig file :
  
gtray
  
this file ask me for username / passwd ...
I entered the one of gmail...
I guess It'll work, but still not sure
  
My question is as follows: 
Would you know were do I have to copy these files ... in /usr/ something ???
  
Thank you very much, 

Best regards, 

Patrick

---

### Post by patrick295767 on 2005-10-21
If I understand well the SRC, sources files , 
have always to be copied to the /usr / sthg ????
   
second question: there was a MAKEFILE 
in the SRC folder, 
is it possible to do the make, make install and so on ... 
 I dont undersstand much about this MAKEfile yet...
  
Thank you very much

Pat'

---

### Post by Gustav on 2005-10-21
The usual way to install tar.gz-files is to first extract the file:
```
tar xvfz filename.tar.gz
```
enter the new directory
```
cd new_folder (mostly new_folder = filename)
```
configure, make and install
```
./configure
make
sudo make install
```
then it should be installed if everything went well

---

### Post by Gustav on 2005-10-21
Or you can install gmail-notify (if you're on breezy)

```
sudo apt-get install gmail-notify
```

---

### Post by patrick295767 on 2005-10-21
[QUOTE=Gustav]Or you can install gmail-notify (if you're on breezy)

```
sudo apt-get install gmail-notify
```[/QUOTE]
  
Thank you **very **much !!!

(I'll try tonight !)

---

### Post by patrick295767 on 2005-10-22
[QUOTE=patrick295767]Thank you **very **much !!!

(I'll try tonight !)[/QUOTE]


I got thsi in my xterm :

Configured to install in /usr/local
Use ./configure <prefix> to specify a different prefix
  
What should i use for prefix ?

thank you very much,

With my best regards, 

adn greetigns from belgium !

---

