---
title: "[SOLVED] Error message"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by irishy on 2007-11-21
Help please
I have an error message on the panel it says (error occurred please run package manager erro broken count >0' can anyone tell me what to do or point me in the right direction 
thanks

---

### Post by overdrank on 2007-11-21
> **irishy said:**
> Help please
I have an error message on the panel it says (error occurred please run package manager erro broken count >0' can anyone tell me what to do or point me in the right direction 
thanks

Hi, You can fix broken packages in synaptic manager located under system, administration, synaptic. In synaptic manager then under edit is fix broken packages

---

### Post by irishy on 2007-11-22
Thanks for your help 
I reckon I am half way there now I just need pointing in the right direction  to be able to work out what commands to use to do this
thanks

---

### Post by zvacet on 2007-11-22
If you are in synaptic under edit you must see **fix broken packages **option.Click on it.

---

### Post by irishy on 2007-11-27
Sorry for the late response to your posts I am following what is being said (I think) when I open up manager I have a statement that states E dpkg was interrupted run dpkg configure a to 
E:cache->open () failed please report and so the option to select edit is not available sorry to sound hopeless but can you tell me what my next move is 
thanks

---

### Post by PmDematagoda on 2007-11-27
Do as the error message suggested, do:-

```
sudo dpkg --configure -a
```

---

### Post by alienexplorers on 2007-11-27
run in terminal:
> sudo dpkg --configure -a

---

### Post by irishy on 2007-11-28
I thank you all very much I have now got over that hurdle and repaired allthe broken packages
thanks

---

