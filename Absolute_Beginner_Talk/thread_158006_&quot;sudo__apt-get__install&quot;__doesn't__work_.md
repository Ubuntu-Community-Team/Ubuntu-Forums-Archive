---
title: "&quot;sudo  apt-get  install&quot;  doesn't  work  correctly"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by gardara on 2006-04-10
Hello,  I'm  pretty  new  to  ubuntu,  just  installed  it  on  my  laptop  last  friday...  Everything  has  been  going  well  until  I  tried  the  "sudo  atp-get  install"  command.
I  have  tried  sudo  apt-get  install  mplayer  and  many  other  applications.  
This  is  what  I  do.
sudo  apt-get  install  mplayer
Reading  package  lists...  Done
Building  dependency  tree...  Done
E:  Couldn't  find  package  mplayer
I  allways  end  up  with  this.  "E:  Couldn't  find  package"  


Am  I  doing  something  wrong?  Please  help  me  as  I  don't  know  what  I  can  do...  I  have  done  some  google-ing  but  haven't  found  any  solution...  

thanks  in  advance  :)

---

### Post by christhemonkey on 2006-04-10
Do you have extra repositories enabled?
See here for a guide:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by ubernoob on 2006-04-10
what is the output of: apt-cache search mplayer

---

### Post by sYs^ on 2006-04-10
You will have to enable some extra repositories.
[https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=AddingMultimediaRepositories#head-5be95103ff75d442c031184440fc53892140eead](https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=AddingMultimediaRepositories#head-5be95103ff75d442c031184440fc53892140eead)

edit: I was damn slow again :p

---

