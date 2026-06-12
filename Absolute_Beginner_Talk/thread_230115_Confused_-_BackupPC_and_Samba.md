---
title: "Confused - BackupPC and Samba"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by flycast on 2006-08-05
I have Samba configured and am working on BackupPC.
I have one Ubuntu box, two XP boxes and soon to have a Mac box on the network.

I have sucessfully executed a backup of the Ubuntu box using BackupPC. The problem is now the XP boxes.

I have a share on the Ubuntu box and can browse from XP boxes. I have a share on the XP box (called gandolf) and I can browse gandolf from my Ubuntu box. gandolf has a shared folder called "SharedDocs" and I can browse, read, write.

I am getting the following error in the gandolf log file:
> tree connect failed: NT_STATUS_BAD_NETWORK_NAME"
My host file looks like this:
> ubuntu	0	backuppc
gandolf	0	backuppc
My gandolf.pl file looks like this (without comments):
> $Conf{SmbShareName} = [ 'gandolf' ];
$Conf{SmbShareUserName} = 'removed for security purposes';
$Conf{SmbSharePasswd} = 'removed for security purposes';
#$Conf{TarShareName} = '/';
$Conf{FullPeriod} = 6.97;
$Conf{IncrPeriod} = 0.97;
$Conf{FullKeepCnt} = 1;
$Conf{FullKeepCntMin} = 1;
$Conf{FullAgeMax}     = 90;
$Conf{IncrKeepCnt} = 6;
$Conf{IncrKeepCntMin} = 1;
$Conf{IncrAgeMax}     = 30;
$Conf{PartialAgeMax} = 3;
$Conf{IncrFill} = 0;
$Conf{RestoreInfoKeepCnt} = 10;
$Conf{ArchiveInfoKeepCnt} = 10;
$Conf{BackupFilesOnly} = ['/SharedDocs']; 
$Conf{BackupFilesExclude} = undef;
$Conf{BlackoutBadPingLimit} = 3;
$Conf{BlackoutGoodCnt}      = 7;
$Conf{BlackoutPeriods} = [
    {
	hourBegin =>  7.0,
	hourEnd   => 23,
	weekDays  => [1, 2, 3, 4, 5],
    },
];
$Conf{BackupZeroFilesIsFatal} = 1;


Any help would be appreciated.
Thanks,
Eric

---

### Post by flycast on 2006-08-06
Nobody out there who knows BackupPC, Samba and XP clients?

---

