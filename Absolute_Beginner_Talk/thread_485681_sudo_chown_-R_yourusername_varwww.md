---
title: "sudo chown -R yourusername /var/www"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by manuleka on 2007-06-27
just installed apache php mysql, phpmyadmin and i ran
```

sudo chown -R yourusername /var/www

```
for permissions

when i add folders to this www folder, i am unble to see them on my localhost 
```

403 forbidden warning/error

```

but i can see my apache2-default folder and when open it i can see the idex.html file....

what do i need to do to make my added folders displayable through my browser?

thanks for any help

---

### Post by phizikal on 2007-06-27
Try using...
```
 sudo chmod +rw /var/www 
```

xx use the one below xx

---

### Post by phizikal on 2007-06-27
Oops I meant.
```

sudo chown YOURUSERNAME /var/www

```

---

### Post by Elijah on 2007-06-27
try chmod and see if that works: 

*sudo chmod 755 -R /var/www/ *

Setting groups may work too: 

*sudo chown yourusername:apache -R /var/www/*

---

### Post by manuleka on 2007-06-27
> **phizikal said:**
> Oops I meant.
```

sudo chown YOURUSERNAME /var/www

```

have tried that.... not working...

---

### Post by manuleka on 2007-06-27
> **Elijah said:**
> try chmod and see if that works: 

*sudo chmod 755 -R /var/www/ *

Setting groups may work too: 

*sudo chown yourusername:apache -R /var/www/*

this one fixed it, thankyou so much

---

