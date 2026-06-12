---
title: "appears no choice for any language support in login screen(except default)"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by offline on 2007-09-19
When I installed ubuntu 6.06LTS(from an original cd) I choose english as my language. Then in login screen there  would appear a list with any variations of english(australia, botswana,...etc only)for me to choose but NO other languages. The same on desktop system>language support.  

 But later reading all the fuss about being able to choose  any language at any time I uninstalled(from the laguage support window) the english language itself(with the secret  hope that some window would popup and give me some language choices to select.

Now I am with a system without any language!!

How can I reinstall english and any other language please??

I have no internet conection in my ubuntu pc but can have access to internet with my other pc(windows)

---

### Post by jamvegan on 2007-09-19
I assume that you installed from a CD?  If you have that CD, you can open the Synaptic Package Manager (System->Administration->Synaptic Package Manager), then go to the Settings menu and choose Repositories.  Insert your Ubuntu CD and choose it as a source.  Close the Software Sources window.  Click the Search button and search for language support.  Install the language-pack and language-support packages for the language(s) you desire.  I think that should do it. :-)

---

### Post by offline on 2007-09-19
> **jamvegan said:**
>  Insert your Ubuntu CD and choose it as a source.  

How? Do you mean repositories>add cd ? And deselect any other sources there?

[QUOTE=jamvegan]Close the Software Sources window.[/QUOTE]

 Add repository window I assume

[QUOTE=jamvegan]Click the Search button and search for language support.[/QUOTE]  

From the open synaptic window? Search what, language-support-en or language-pack-en

Thanks.:-\"

---

### Post by jamvegan on 2007-09-19
Sorry, I'm running 7.04, so some things are apparently named a little bit differently.  Everything you suggest sounds right.  Yes, the search button in Synaptic.  If you do a search on "language support" against names and descriptions (which is the default type of search, at least on my system), it will list more than you need, but will include all of the files that I believe that you need.  At minimum, you would want to install language-support-en and language-pack-en.  Since this all started with you wanting to try language support for other languages, I thought that you might want to be able to choose from the complete list. :-)

---

