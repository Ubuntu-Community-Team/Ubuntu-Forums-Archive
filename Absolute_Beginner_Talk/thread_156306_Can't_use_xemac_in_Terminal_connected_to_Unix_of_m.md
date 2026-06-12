---
title: "Can't use xemac in Terminal connected to Unix of my school."
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by longtran79 on 2006-04-06
Hi all, Im a newbie in Ubuntu. After I update Xemacs using Synaptic, i can use it in terminal. If I connect teminal to my school Unix system, I could not use it. Please tell me how to configure the system to work. I thank you a lot!!!!!!!
](*,) ](*,) ](*,)

---

### Post by IYY on 2006-04-06
Are you using SSH to connect? If so, you don't have to have the program installed at home, but you do have to have it installed in school. If that is the case, you need to connect like this

ssh -X -l username address

---

### Post by longtran79 on 2006-04-07
I try what you said and get this error:
longtran79@ubuntu:~$ ssh -X -l [email]lon1@linux.gl.umbc.edu[/email]
usage: ssh [-1246AaCfgkMNnqsTtVvXxY] [-b bind_address] [-c cipher_spec]
           [-D port] [-e escape_char] [-F configfile]
           [-i identity_file] [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [user@]hostname [command]
 any help will appreciate!!!:confused: :confused:

---

### Post by oscar on 2006-04-07
it should be:
ssh -X -l lon1 linux.gl.umbc.edu
not 
ssh -X -l [email]lon1@linux.gl.umbc.edu[/email]

---

### Post by steve.horsley on 2006-04-07
[QUOTE=oscar]it should be:
ssh -X -l lon1 linux.gl.umbc.edu
not 
ssh -X -l [email]lon1@linux.gl.umbc.edu[/email][/QUOTE]
or:
```
ssh -X lon1@linux.gl.umbc.edu
```

---

### Post by longtran79 on 2006-04-10
it works great!!!!thanks you guys!!!\\:D/

---

