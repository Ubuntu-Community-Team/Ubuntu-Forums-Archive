---
title: "&quot;Dependency is not satisfiable libc6&quot; error"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by zmr on 2006-12-08
I am trying to install the pppoe using a deb package I downloaded from the Ubuntu package site in order to get my internet connection working in Ubuntu. When I start the deb file it says "Dependency is not satisfiable: libc6". Normally I would take this to mean that I need to download the libc6 deb and install that first, but my understanding is that libc6 is already installed (because so many programs depend on it--openoffice etc). Other threads in the Ubuntu forums have suggested that people with similar problems use synaptic. But, with no internet connection, it's not possible to access anything using synaptic. How can I install pppoe while getting the installer to recognize that libc6 is already installed? (I am having the same error with the uim-m17n deb file too.)

Thanks..
zach

---

### Post by ajgreeny on 2006-12-08
Why are you downloading to install and not letting apt-get, aptitude or synaptic do the job for you.  They will sort out your dependency problems automatically, and install whatever is needed without you needing to search for anything.

Sorry zmr, I missed your comment about not having internet connection.

---

### Post by loell on 2006-12-08
> **ajgreeny said:**
> Why are you downloading to install and not letting apt-get, aptitude or synaptic do the job for you.  They will sort out your dependency problems automatically, and install whatever is needed without you needing to search for anything.

because he can't use synaptic if he is disconnected.

hi, zach, maybe that package is meant for debian, or older versions of ubuntu , usually at the download page, it will be stated on what version deb package is built for.

---

### Post by zmr on 2006-12-08
Thank you loell and ajgreeny. 

loell, I believe the deb files I downloaded came from the Edgy package, though I am using Dapper. Perhaps I should get the libc6 for Edgy? I will try that now.

---

### Post by loell on 2006-12-08
i think thats a no no ;) 

it will likely break your system

you can


```
sudo pppoeconf
```

if you are trying to configure your dsl connection

---

### Post by zmr on 2006-12-08
ha ha. Thanks for the quick heads up. Can I access pppoeconf without installing pppoe? Is there some pppoe functionality already in dapper? Is a major problem if I install packages found in Edgy on Dapper -- (for example, I really need access to Tibetan input methods using uim-m17n, but did not see a uim-m17n package in dapper. Is it terribly difficult to upgrade to edgy from Dapper? (Note I am in a remote area of Tibet with a so so internet connection, so downloading another large ISO file for Edgy is not really a viable option)

Thanks!

---

### Post by loell on 2006-12-08
yeah pppoe is already preinstalled in dapper, that is why there is pppoeconf for conifuring pppoe.

---

### Post by zmr on 2006-12-08
sorry.. i changed part of the last reply i wrote while you were responding... I will go ahead and try pppoeconf. Thanks again.

Maybe you can tell i am complete beginner on linux :)

---

### Post by loell on 2006-12-08
oh, you are living Tibet, wow, :KS

so what is your type of connection, there? are you trying to use ubuntu on dsl?

---

### Post by zmr on 2006-12-08
Yes. It's basically a dsl connection, though it's the whole process of establishing a connection with the internet service provider is in Chinese (not Tibetan) so I am not entirely sure about the specifics of the connection and what we might term it according to international conventions. It appears basically to be dsl, hence the need to work with pppoe...

---

### Post by loell on 2006-12-08
here is one of the many how tos in "ubuntu + dsl" just googled it a while ago
 :) 

[http://pranni.wordpress.com/2006/10/16/configuring-dsl-with-ubuntu/]("http://pranni.wordpress.com/2006/10/16/configuring-dsl-with-ubuntu/")

---

### Post by zmr on 2006-12-08
Now it is working perfectly. (I am connected using Ubuntu now). Thanks for the link! :)

---

### Post by loell on 2006-12-08
your welcome, spread the word in Tibet :KS

---

### Post by zmr on 2006-12-10
> **loell said:**
> your welcome, spread the word in Tibet :KS
no joke. if ubuntu supported tibetan there would be wide use for it here, although Windows vista already may be a step ahead...

---

### Post by loell on 2006-12-10
when you say tibetan input, do you mean Dzongkha input? are they the same?

---

### Post by loell on 2006-12-10
there is an on going effort to incorporate Dzongkha in ubuntu

[https://launchpad.net/people/ubuntu-l10n-dz]("https://launchpad.net/people/ubuntu-l10n-dz")

but i think its far from being done. you can also volunteer to help for the translation

---

### Post by zmr on 2006-12-10
Dzongkha is indeed related to Tibetan (they are in the same language family and basically use the same scripts). There are  two emerging standards, however, for using Tibetan-style scripts digitally--one sponsored by the Bhutanese government using Dzongkha and one influenced by a broader international community that is more general. Dzongkha has its own defined keyboards and fonts (and may have its own unicode encoding separate from Tibetan-- not sure). It's interesting to see a project standardizing Dzongkka for Linux, given that the initiative to incorporate Dzongkha into Vista fell through (see article [here]("http://www.kuenselonline.com/modules.php?name=News&file=article&sid=7057") if interested). The effort for non-Dzongkha (unicode) Tibetan in Vista, however is going strong-- backed in part by Peoples Republic of China. 

Anyways, its exciting to see efforts to use Dzongkha in linux. Hopefully standard international Tibetan unicode can follow closely after, perhaps even working with Dzongkha translators. 

thanks for the link!

---

### Post by erizo on 2007-06-13
Got the same error in feisty fawn.
any suggestion?

---

