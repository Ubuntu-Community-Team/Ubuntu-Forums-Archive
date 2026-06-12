---
title: "wget; connection reset by peer!"
date: 2013-04-09
forum: Any Other OS
---

### Post by Si1414 on 2013-04-09
I am using the following code to download a list of pdf files:

```
wget -i list.txt -A .pdf

```
Some pdf files are downloaded properly. However, some pdf files are not downloaded properly. When I check the log, I see the following error:

```
--2013-04-09 11:25:42--  http://amazon.com/111.pdf
Reusing existing connection to amazon.com:80.
HTTP request sent, awaiting response... 200 No headers, assuming HTTP/0.9
Length: unspecified
Saving to: `111.pdf'


    [                                         <=>       ] 1,045       --.-K/s   in 2m 9s


2013-04-09 11:27:51 (8.11 B/s) - Read error at byte 1045 (Connection reset by peer).Retrying.


--2013-04-09 11:27:52--  (try: 2)  http://amazon.com/111.pdf
Connecting to amazon.com (amazon.com)|00.00.55.888|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2680728 (2.6M) [application/pdf]
Saving to: `111.pdf'


61% [==============================>                    ] 1,649,221   10.0K/s   in 2m 41s


2013-04-09 11:30:41 (10.0 KB/s) - Read error at byte 1649221/2680728 (Connection reset by peer). Retrying.


--2013-04-09 11:30:43--  (try: 3)  http://amazon.com/111.pdf
Connecting to amazon.com (amazon.com)|00.00.55.888|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2680728 (2.6M) [application/pdf]
Saving to: `111.pdf'


100%[==================================================>] 2,680,728   10.1K/s   in 4m 22s


2013-04-09 11:35:11 (10.0 KB/s) - `111.pdf' saved [2680728/2680728]



```


I wonder why I can not open the pdf file 111.pdf? The above report says that it is 100% downloaded. Is it because of the connection reset by the peer?

I wonder if it is possible to put the wget in a loop for every file, in such a way that it does not exit the loop, until the download is done with no error?
I found the following loop, however, it gives an error. The code and the error is shown below:

Code:
```
while read -r link
do
        wget -A .pdf
        until [ $? = 0 ]
        do
            wget -A .pdf
        done
done < ./list.txt

```

Error:
```
Try `wget --help' for more options.
wget: missing URL
Usage: wget [OPTION]... [URL]...

```
I am using Cygwin on Windows.

Thank you for your help.

---

### Post by Si1414 on 2013-04-15
*Hint for people who are interested:*
I increased the download speed to 100K and also increased the random wait time between downloads. Apparently, this solves the problem.

---

