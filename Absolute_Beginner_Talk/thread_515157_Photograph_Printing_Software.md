---
title: "Photograph Printing Software"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by thedivvyman on 2007-08-01
I  am  looking  for  software  that  allows  me  to  make  one   print   on  A4  photo  paper or  two  prints,  or  four  prints  etc.  
Most  software  that  comes  with  digital  cameras  have  this  facility,  but  of  course  they  are  all  windows  based.

If  anyone  knows  if  there  is  anything  like  this  for  Ubuntu,  I  would  appreciate  any  info.

Thanks

---

### Post by apswartz on 2007-08-01
Check this out...
[http://www.blackfiveservices.co.uk/photoprint.shtml](http://www.blackfiveservices.co.uk/photoprint.shtml)

I've never used it. Let us know if it works as you wish.

---

### Post by apswartz on 2007-08-01
Actually, it seems to be in the repository...
sudo apt-get install photoprint

---

### Post by linuxwizard on 2007-08-01
[http://gphoto.sourceforge.net/](http://gphoto.sourceforge.net/)

---

### Post by thedivvyman on 2007-08-02
Thanks - photoprint  sounds  just  the  job.  Can  anyone  explain  how  to  install  it  onto  Ubuntu.  I  have  had  Ubuntu  installed  for a  while  now  but  I  am  not  good  at  technical stuff.  If  you  follow  the  link  below  it  does  say  some  other  stuff  has  to be  installed.  Any  info  leading  to  a  successful  install  of  photoprint would  be  fantastic.

Thanks  again


[http://www.blackfiveservices.co.uk/photoprint.shtml](http://www.blackfiveservices.co.uk/photoprint.shtml)

---

### Post by apswartz on 2007-08-02
> **thedivvyman said:**
> Any  info  leading  to  a  successful  install  of  photoprint would  be  fantastic.

Try this...

sudo apt-get install photoprint

That will also install the necessary dependancies

---

### Post by thedivvyman on 2007-08-02
Hi  thanks  for  your  reply -  but  when  I  input  your  command  I  get  this..............

brian@brian-desktop:~$ sudo apt-get install photoprint
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package photoprint
brian@brian-desktop:~$
 
Any  help  would  be  welcome

Thanks

---

### Post by apswartz on 2007-08-02
Hmmmm...

use the instructions found here...
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)
to install medibutu. Then try again to install the program.

---

### Post by rax_m on 2007-08-02
Hi 

You have to make sure that you enable your "universe" repository before the command will work as the package is in the universe repository. 

You can do that from the System->Administration->Software Sources

Cheers
Rax

---

### Post by thedivvyman on 2007-08-02
Thanks for  replies - no  sign  of  software  sources  in  administration - i  have  software  properties,  but  can't  find  software  sources.

I  followed  the  link  but  couldn't  understand  how  it  will  help  with  what  I  am  doing.  Thanks  again
really  appreciated

---

### Post by apswartz on 2007-08-02
Open up your Synaptic package manager. If you have to press Alt-F2 and type in  the word **synaptic** and press** enter**.

On the menu bar, click on **Settings** and then select **Repositories.**

On the tab that says** Ubuntu Software**, make sure that the first four checkboxes are selected.

The try installing the software.

---

### Post by thedivvyman on 2007-08-02
Hi -  thanks  for  persevering,  but  went  into  synaptic  manager - repositories but  there  is  no  tab  with  ubuntu  software, if  you  can  offer  more  help,  I  would  appreciate  it  if  you  could  type  it  into  a  private message  for  me  as  I  am  about  to  close  my  machine  down  and  am  away  now  until  Monday.  
Thanks  again  for  patience  so  far  though.
Regards

---

### Post by apswartz on 2007-08-02
Okay, what version of Ubuntu are you using?

---

### Post by apswartz on 2007-08-02
Ignore the attachment in the last message (sources.zip). It is my sources.list file, but it is for Feisty and it doesn't sound like you are using Feisty.

---

### Post by thedivvyman on 2007-08-07
Hi  -  I  have  read  through  this  thread  after  coming  back  from  a  weekend  break,  but  have  had  no  luck  installing  Photoprint  software.
apswartz -  As  far  as  I  know  I  am  using  Ubuntu 6.06,  but  if  you can  point  me  to  where  I  can  check  this  out,  it  would  be  great.

I  would  just  like  to  thank  everyone  on  this  forum  for  their  dedication  and  general help  they  give.  Most  people  struggle  with  Ubuntu  installs,  but  thanks  to  you  guys,  they  percevere - please  keep  it  up  and  thanks  again.

---

### Post by apswartz on 2007-08-07
Here is the thread you want to carefully read to get all of your repositories activated.
[http://ubuntuforums.org/showthread.php?t=185758](http://ubuntuforums.org/showthread.php?t=185758)

Once you do this you should be able to install the software IF it has been backported to Dapper.

---

