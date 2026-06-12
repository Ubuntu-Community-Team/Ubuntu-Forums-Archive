---
title: "building a driver"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by determinedblkman1 on 2007-11-22
if i built a driver (ethernet controller) using linux, could i take the source code and recompile it using an independent compiler and use it for windows?

---

### Post by elctb on 2007-11-24
No without making changes to the source code. The windows driver api is different than linux's. Most of the driver code is applicable to both windows and linux since it deals with the ethernet controller, but the part that deals with the OS (linux/windows) would need to be changed.

---

### Post by determinedblkman1 on 2007-11-24
(theoreticaly) lets say i take the souce code and compile it on/with a (lets say 'dev-c' )compiler that's on my windows partition;  since they're both (linux / windows) using the same etho controller do you thing it would work? -- i know one response said something about "api", but i dont really understand the role of the "api" (i came across it in my studies but i haven't grasped it just yet)

---

### Post by LaRoza on 2007-11-24
It doesn't work that way. If you don't know what an API is, you should hold back on programming drivers until you have a little more experience.

---

### Post by determinedblkman1 on 2007-11-24
ok, (i googled it-- tell me if i'm right or wrong) an api is (like) the equivelent of a linux lib. file (for windows)- and when the program is looking for for command instructions (so to say) it'll look in the wrong place?

---

### Post by elctb on 2007-11-24
API stands for Application Programming Interface. But what does this mean ? It's really a convention on how applications use the kernel resources.

For example, lets assume you write your own kernel and decide that for drivers to register with the kernel they need to call a function named "determinedblkman1_register()" and hence you create your own API. If a windows driver doesn't call "determinedblkman1_register()" your kernel will never know the driver has been loaded. That's what happens with windows and linux. They have a different API. All linux drivers register their services with the kernel via a set of specific functions or API. To register with windows a different set of functions need to be used instead. You don't need to change the code that uses the ethernet controller, but the code that interfaces with the kernel.

---

