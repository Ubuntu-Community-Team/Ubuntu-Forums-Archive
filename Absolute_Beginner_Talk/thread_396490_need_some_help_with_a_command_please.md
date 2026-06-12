---
title: "need some help with a command please"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by klein de usa on 2007-03-29
hi 
i need a little help, i messed up my xorg.conf file i do have a back up but i can't seem to get it renamed , i'm using the the ubuntu 6.10 cd in rescue mode i'm at a shell prompt and i need to rename a file, when i type remane in at the prompt it returns usage: rename [-v] [-n] [-f] per lexpr [filenames] then it puts me back to a prompt # 
i would like to rename /etc/X11/axorg.conf to /etc/X11/xorg.conf could some one help me with the comand i need ?

---

### Post by chamberlain2006 on 2007-03-29
The command is: 

sudo mv /etc/X11/axorg.conf /etc/X11/xorg.conf

---

### Post by klein de usa on 2007-03-29
thank you very much 
i tried that and it didn't work not because it was wrong but because i wasn't closing the  shell in the right way,:
#sync ;sync      hit enter
#exit                 hit enter

it still locked up and wouldn't select reboot but i manuly rebooted it and it came up just fine 

i think sudo cp /etc/X11/aorg.conf xorg.conf  would work too but i wasn't closing the terminal in the correct way, this is where i found my mistake:
[http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/]("http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/") 
thank you

---

