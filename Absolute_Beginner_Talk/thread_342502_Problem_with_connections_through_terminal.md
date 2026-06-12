---
title: "Problem with connections through terminal"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Ic3y on 2007-01-20
Hey all,

Hit a brick wall again ](*,) 
I am having some problems with my terminal I have tried to use apt-get update and when it gets to the security update server download it times out constantly here is an extract of what the timeout says 
>   Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

Is there anyway I can fix this as I believe it is trying to connect through LAN router port 1.0.0.0

Thanks in advance
Ic3y :biggrin:

---

### Post by JamieC on 2007-01-20
Can you access the address using a browser? Click [here](http://archive.ubuntu.com), do you see a directory listing?

---

### Post by Ic3y on 2007-01-20
yeah i can access the directory 
I had to disable IPv6 through firefox though if that is affecting the connection via the terminal
any ideas?!?!

Thanks again for the response
Ic3y :biggrin:

---

### Post by JamieC on 2007-01-20
You could try using a proxy, open a new terminal and type the following (where <editor> is your preferred editor, vim, gedit, etc):
```

sudo <edtior> /etc/apt/apt.conf

```

Find the IP of a proxy and add the following lines to the bottom of the file, ensuring you save it:
```

ACQUIRE {
  http::proxy "http://<ip>:8080/"
}

```

Then type:
```

sudo apt-get update

```

---

### Post by Ic3y on 2007-01-20
worked a treat that new problem though how would i get around this

> [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]


gotta connect to both of these servers tried the way you mentioned but comes back with

> E: Syntax error /etc/apt/apt.conf:4: Extra junk after value


what would i do in this instance

these are the configurations that I have tried so far
> ACQUIRE {
  http::proxy "http://195.248.90.35:8080/"
}

ACQUIRE {
  http::proxy "http://82.211.81.138:8080/"
}


> ACQUIRE {
  http::proxy "http://195.248.90.35:8080/"
  http::proxy "http://82.211.81.138:8080/"
} 
I get the junk error with this second one and I can only connect to one server with the other way that being the [http://82.211.81.138:8080](http://82.211.81.138:8080)

Thanks again JamieC

Ic3y :biggrin:

---

### Post by Ic3y on 2007-01-20
never mind took a pot shot at something else and it worked chose the archive.ubuntu.com with port 80 as a pose to 8080 and it worked a treat \\:D/ 

Thanks for all your help much appreciated

Ic3y :biggrin:

---

### Post by JamieC on 2007-01-20
What did you use to edit it? Your apt configuration file has something that should not be there, can you attach it please?

Actually, try using just one proxy configuration...

---

### Post by Ic3y on 2007-01-20
I used gedit 

this is the configuration that I used

> ACQUIRE {
http::proxy "http://195.248.90.35:80/"
}

I know that with the webserver port some routers are touchy with the 80 and 8080 ports 

:D

Thanks again
Ic3y :biggrin:

---

### Post by JamieC on 2007-01-20
You're very welcome, glad you've got it working!

---

### Post by Heppie on 2007-01-21
im having the same problem. but on my ubuntu apt.conf does not exist it creates a new file. what do i do?

---

### Post by Ic3y on 2007-01-21
mine was a new file as well I just pasted the code in there and edited it accordingly 

If you have more problems ask and I will see what I can do for you

Regards
Ic3y :biggrin:

---

### Post by Heppie on 2007-01-21
worked cheers:D

---

