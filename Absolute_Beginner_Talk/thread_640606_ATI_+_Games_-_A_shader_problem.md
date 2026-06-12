---
title: "ATI + Games - A shader problem"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Scarath on 2007-12-14
I have ATI  graffics which work with the ubuntu restricted drivers. All desktop effects etc work with them.

I install the newer drivers from the ATI website and it messed up the computer and made it slow and choppy so i went back to the restricted drivers u get with ubuntu. 

Anyway when i install a game and try to run it it gives me a shader error (cannot run unsupported shaders install new drivers etc etc) . This happened with both the new drivers i installed and the ubuntu repo ones. 

Any solutions?

---

### Post by ajopaul on 2007-12-14
which game ? is it linux native or are you trying with WINE/CEDEGA?

---

### Post by flamelab on 2007-12-14
> **Scarath said:**
> I have ATI  graffics which work with the ubuntu restricted drivers. All desktop effects etc work with them.

I install the newer drivers from the ATI website and it messed up the computer and made it slow and choppy so i went back to the restricted drivers u get with ubuntu. 

Anyway when i install a game and try to run it it gives me a shader error (cannot run unsupported shaders install new drivers etc etc) . This happened with both the new drivers i installed and the ubuntu repo ones. 

Any solutions?

Make sure you have ONLY the repos' driver installed by typing

```
fglrxinfo 
```

there you should see that 8.37 driver is installed .

Then , stop desktop effects and start the game .

Tell us what happens .

---

### Post by Scarath on 2007-12-14
> which game ?

Penumbra: Overture, its a native linux game. Im jst testing the demo, tryin to get it working
[http://www.penumbra-overture.com/demo.php](http://www.penumbra-overture.com/demo.php)
```

fglrxinfo
```

Shows i do just have the 8.37 driver installed

Shut off desktop effects, sudo ./the game and ...
> 
Error you graphics card does not support vertex shaders
Please try getting new ones etc etc 

thanks

---

### Post by Scarath on 2007-12-14
ok so update, i tried some other games on it to see how the comp liked 3D in general.

I tried Open arena = result = worked ok with some wierdness in the rendering

Warsow = This came up with an error = your open GL installation does not support direct rendering, downloaddrivers etc etc

Arnt the drivers in the repos ment to deal with this sort of thing? 

Im new to ATI :D

---

### Post by Scarath on 2007-12-14
sorry but 'bump'

---

### Post by Scarath on 2007-12-15
one last try - bump

---

