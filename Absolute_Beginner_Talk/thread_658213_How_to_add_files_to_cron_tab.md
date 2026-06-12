---
title: "How to add files to cron tab?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by perpetual_dream on 2008-01-04
Hello,

I am an absolute beginner I have installed ubuntu a week ago bc I need to run a  script on linux.

My script installation guide requires the following:

12. Cron settings
~~~~~~~~~~~~~
Files needs to be added in crontab are in folder cron/
1. videoEncodeCron.php (recommended duration: 1 Minute)
2. deleteTrashMail.php (recommended duration: 24 hours)
3. groupDeleteCron.php (recommended duration: 24 hours)
4. groupPhotoDeleteCron.php (recommended duration: 2 hours)
5. groupVideoAutoActivateCron.php (recommended duration: 1 Minute)
f6. groupVideoDeleteCron.php (recommended duration: 2 hours)
7. groupVideoEncodeCron.php (recommended duration: 1 Minute)
8. musicAutoActivateCron.php (recommended duration: 1 Minute)
9. musicDeleteCron.php (recommended duration: 2 hours)
10. musicEncodeCron.php (recommended duration: 1 Minute)
11. photoDeleteCron.php (recommended duration: 2 hours)
12. updateVideoTagCount.php (recommended duration: 2 hours)
13. userDeleteCron.php (recommended duration: 24 hours)
14. videoAutoActivateCron.php (recommended duration: 1 Minute)
15. videoDeleteCron.php (recommended duration: 2 hours)
*/5 * * * * curl --get [http://yourdomain.com/cron/videoEncodeCron.php](http://yourdomain.com/cron/videoEncodeCron.php) > /dev/null
*/5 * * * * curl --get [http://yourdomain.com/cron/newsLetterCron.php](http://yourdomain.com/cron/newsLetterCron.php) > /dev/null
59 */2 * * * curl --get [http://yourdomain.com/cron/videoDeleteCron.php](http://yourdomain.com/cron/videoDeleteCron.php) > /dev/null
* * * * * curl --get [http://yourdomain.com/cron/videoAutoActivateCron.php](http://yourdomain.com/cron/videoAutoActivateCron.php) > /dev/null
59 23 * * * curl --get [http://yourdomain.com/cron/userDeleteCron.php](http://yourdomain.com/cron/userDeleteCron.php) > /dev/null
59 */2 * * * curl --get [http://yourdomain.com/cron/updateVideoTagCount.php](http://yourdomain.com/cron/updateVideoTagCount.php) > /dev/null
59 */2 * * * curl --get [http://yourdomain.com/cron/photoDeleteCron.php](http://yourdomain.com/cron/photoDeleteCron.php) > /dev/null
* * * * * curl --get [http://yourdomain.com/cron/musicEncodeCron.php](http://yourdomain.com/cron/musicEncodeCron.php) > /dev/null
59 */2 * * * curl --get [http://yourdomain.com/cron/musicDeleteCron.php](http://yourdomain.com/cron/musicDeleteCron.php) > /dev/null
* * * * * curl --get [http://yourdomain.com/cron/musicAutoActivateCron.php](http://yourdomain.com/cron/musicAutoActivateCron.php) > /dev/null
*/5 * * * * curl --get [http://yourdomain.com/cron/groupVideoEncodeCron.php](http://yourdomain.com/cron/groupVideoEncodeCron.php) > /dev/null
* * * * * curl --get [http://yourdomain.com/cron/groupVideoAutoActivateCron.php](http://yourdomain.com/cron/groupVideoAutoActivateCron.php) > /dev/null
59 */2 * * * curl --get [http://yourdomain.com/cron/groupVideoDeleteCron.php](http://yourdomain.com/cron/groupVideoDeleteCron.php) > /dev/null
59 */2 * * * curl --get [http://yourdomain.com/cron/grouphhotoDeleteCron.php](http://yourdomain.com/cron/grouphhotoDeleteCron.php) > /dev/null
59 23 * * * curl --get [http://yourdomain.com/cron/deleteTrashMail.php](http://yourdomain.com/cron/deleteTrashMail.php) > /dev/null
59 23 * * * curl --get [http://yourdomain.com/cron/groupDeleteCron.php](http://yourdomain.com/cron/groupDeleteCron.php) > /dev/null

How to execute this commands???

for example when i type this command in the terminal:
 59 */2 * * * curl --get [http://localhost/xxxx/cron/groupVideoDeleteCron.php](http://localhost/xxxx/cron/groupVideoDeleteCron.php) > /dev/null
i recieve bash: 59: command not found error

Please help with execution of the above curl commands!

---

### Post by kpkeerthi on 2008-01-04
**curl --get [http://localhost/xxxx/cron/groupVideoDeleteCron.php](http://localhost/xxxx/cron/groupVideoDeleteCron.php) > /dev/null** is the command you should type in a terminal

---

### Post by perpetual_dream on 2008-01-04
And how to add the files with the numbers infront of them to the crontab?

---

