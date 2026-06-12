---
title: "Windows Phone and WinSXS"
date: 2012-03-08
forum: Any Other OS
---

### Post by Nikolai D. on 2012-03-08
Hi ppl,

Since some short time ago i realized what for enormous  brake trough for Personal Computer Operating System Software Engineering is a Package Manager technology. I got more interested in the subject. And what for special something n900 is.

So i wonder does Windows Phone OS also has WinSXS folder to? Or is it Android/iOS/OSX like? Where apps are in their own places.

Thanks in advance,
Nikolai

---

### Post by Lucradia on 2012-03-12
I'm sure it does exactly what the WinSXS does on the normal Windows OS, it allows DLLs that are 32-bit or 64-bit to run in either mode, hence the name, "Side-By-Side Configuration." But, SXS Errors usually don't occur often, and are related to not installing the proper bit version of a software. For instance, CamStudio will attempt to run with only the 64-bit version of the Visual C++ 2005/8 library, but will fail saying the "Windows Side-By-Side Configuration is not configured properly" or similar. To remedy this, you must install the 32-bit version as well. This allows both versions to interact with each other, or rather, 32-bit code to be executed on 64-bit terms, and I guess, vice-versa via sloppy conversion.

---

