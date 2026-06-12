---
title: "[SOLVED] external dvd burner"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-24
Looking to build or buy an external dvd/cd burner. Can someone recommend a great tool for burning dvds and cds, like Nero, Roxio, or something along those lines? Do I need a few tools to do what those programs do, or is there one tool that can do it all? A tool with a GUI is preferred, however, not necessary. Any help with this will be greatly appreciated.

---

### Post by taurus on 2007-12-24
K3b, brasero, gnomebaker to name a few.

---

### Post by fmbugdadi on 2007-12-24
can I download those from a repository like synaptic, or do I have to do a manual install?

---

### Post by taurus on 2007-12-24
They are all available from synaptic or apt-get.

```
sudo apt-get update
sudo apt-get install k3b
```

---

### Post by fmbugdadi on 2007-12-24
Thanks

---

### Post by LaRoza on 2007-12-24
> **fmbugdadi said:**
> Looking to build or buy an external dvd/cd burner. Can someone recommend a great tool for burning dvds and cds, like Nero, Roxio, or something along those lines? Do I need a few tools to do what those programs do, or is there one tool that can do it all? A tool with a GUI is preferred, however, not necessary. Any help with this will be greatly appreciated.

```

sudo aptitude install k3b

```

GUI, and better than the ones you listed.

---

### Post by Josh1 on 2007-12-24
If you have used Nero or Ashampoo on Windoze, try using k3b as noted. Best burning software in terms of features IMO.

---

### Post by fmbugdadi on 2007-12-24
O.k. I have downloaded k3b, I have plugged in my DVD burner, which, K3b recognizes. I am having problems burning an AVI video clip into a movie on dvd. Here is what I am doing. 

I choose New Video dvd project, when I do that, KB3, automatically inserts 2 folders in the current project windows called Audio_TS and Video_TS

next, I drag my AVI file to the current projects window.

then, I click on BURN, and an additional window pops up, and I have the option to choose some additional settings. The only thing I change on this screen is, the write speed down to 4x, then I click on burn. When I do, I get 3 errors....

1. The project does not contain all necessary video DVD files. 
2. The resulting DVD will most likely not be playable on a HIFI DVD player.
3. Could not determine size of resulting image file. 

does not let me continue with project.

Does anyone see anything obvious I may be doing wrong?

---

### Post by taurus on 2007-12-24
You should use devede (available from synaptic) to convert your .avi to .iso and then burn the .iso as an image file using k3b to a DVD media.

---

### Post by fmbugdadi on 2007-12-24
I am giving that a shot right now. It is taking a long time for the conversion, but it is progressing.There must be a better way to do this. It has been over 2 hours now for the conversion, and it is at about 77%. hope it works.

---

### Post by fmbugdadi on 2007-12-24
Happy to report that the conversion did work, and the DVD played in my DVD player. Just wish it was not such a long process to convert to ISO before I can burn it a DVD. K3B appears to be a great burning tool.

---

