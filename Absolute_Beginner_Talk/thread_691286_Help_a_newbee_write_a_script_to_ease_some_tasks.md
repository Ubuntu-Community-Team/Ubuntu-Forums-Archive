---
title: "Help a newbee write a script to ease some tasks"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-02-08
Hi
Thank you for reading my post.
I want to write an script :O, the script should do the following tasks:

the overall goal is to write an script to download some files using wget. I have some urls (which I usually download some files from them) that I should use them from behind a proxy and not directly.

I want to write a script which has a list of domains that need proxy and this script should take 2 argument, one is the URL pointing to the file that It should download, second one is equal to -c flag of wget in order to continue a broken download.

the script will decide to use the proxy when calling the wget or not. also It should set the proxy before calling the wget.



Thanks

---

### Post by The Cog on 2008-02-08
This script does it, I think.

Save it as (lets say) xwget and make it executable with this command:
**chmod +x xwget**
Then use it like you would use wget:
**xwget -c [http://www.mydomain.com/myfile](http://www.mydomain.com/myfile)**

You will need to edit the proxyDomains list and the proxy settings at the top of the fiel of course. If you want to do some dry runs first, put a # at the start of the line that says 
**system command**
and remove the ' from the pront statement above. Then it will just print what it was going to do.

```
#!/usr/bin/python

proxyDomains = ["google.com", "ubuntu.com"]
proxy = "1.2.3.4:8000"

import os, sys

args = []
url = ""
for arg in sys.argv[1:]:
    if arg.startswith("-"):
        args.append(arg)
    else:
        url = arg
needProxy = False
for fragment in url.split("/"):
    for domain in proxyDomains:
        if fragment.endswith(domain):
            needProxy = True
            break
if needProxy:
    command = "export http_proxy=" + proxy + " ; wget "
else:
    command = "wget "
    args.append("--no-proxy")
command += " ".join(args + [url])
#print "COMMAND:", command
os.system(command)

```

---

### Post by legolas_w on 2008-02-08
Thank you so much, it could be an start for me to tune the script and learn more.
Is it written in python language?
I thought we use bash to create shell script.

Thanks

---

### Post by johnnyb1726 on 2008-02-08
That script is written in python as you can tell by the first line #!/usr/bin/python.  You can use any scripting language such as python, perl, bash, etc. to create a script.  Python is a good language to learn and Ubuntu comes with a book called "Dive into Python".

---

### Post by The Cog on 2008-02-08
Yes it's in python. I'm rubbish at shell scripting and couldn't figure out how to do a lot of things this script needs to do. 

If you're thinking of learning programming, I do think python might be a good starting point. Shell scripting can be very handy and I wish I were better at it, but I also think (perhaps in ignorance) that it's somewhat limited. It has a different objective (automating running other programs)  to languages like python which are more oriented towards general purpose programming.

---

