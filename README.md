# nostr_console
Nostr console client using Dart

# Use

Easiest way to run nostr_console: Go to releases and get an executable for your platform.

Otherwise do following:
1. Install [Flutter](https://docs.flutter.dev/get-started/install) SDK, or [Dart](https://dart.dev/get-dart) SDK
2. git clone this repository
3. From the project folder, run command ```dart pub get``` which gets all the dependencies
4. Run command ```dart run bin/nostr_console.dart```, which will run it with default settings. 
5. Further you can create an executable for your platform by  ```dart compile exe bin/nostr_console.dart``` which will create an executable for your platform. You can invoke that exe with required parameters. On Windows, you can create a shortcut to it with your desired command line arguments mentioned in it.

Usage: 

```
usage: dart run bin/nostr_console.dart [OPTIONS] 

  OPTIONS

      -p, --pubkey  <public key>    The hex public key of user whose events and feed are shown. Default is a hard-coded
                                    well known private key. When given, posts/replies can't be sent. 
      -k, --prikey  <private key>   The hex private key of user whose events and feed are shown. Also used to sign events 
                                    sent. Default is a hard-coded well known private key. 
      -r, --relay   <relay wss url> The relay url that is used as main relay. Default is wss://nostr-relay.untethr.me.
      -d, --days    <N as num>      The latest number of days for which events are shown. Default is 1.
      -q, --request <REQ string>    This request is sent verbatim to the default relay. It can be used to recieve all events
                                    from a relay. If not provided, then events for default or given user are shown.
      -f, --file    <filename>      Read from given file, if it is present, and at the end of the program execution, write
                                    to it all the events (including the ones read, and any new received).
      -s, --disable-file            When turned on, even the default file is not read from.
      -t, --translate               Translate some of the recent posts using Google translate site ( and not api). Google 
                                    is accessed for any translation request only if this flag is present, and not otherwise.

  UI Options                                
      -a, --align  <left>           When "left" is given as option to this argument, then the text is aligned to left. By default
                                    the posts or text is aligned to the center of the terminal. 
      -w, --width  <width as num>   This specifies how wide you want the text to be, in number of columns. Default is 120. 
                                    Cant be less than 60.
      -m, --maxdepth <depth as num> The maximum depth to which the threads can be displayed. Minimum is 2 and
                                    maximum allowed is 12. 
      -c, --color  <color>          Color option can be green, cyan, white, black, red and blue.
      -h, --help                    Print this usage message and exit.
                               
```                                

To get ALL the latest messages for last 3 days (on linux which allows backtick execution): 

```
nostr_console.exe  --request=`echo "[\"REQ\",\"l\",{\"since\":$(date -d '-3 day' +%s)}]"`
```
 
To get the latest messages for user with private key K ( that is also used to sign posted/sent messages): 
 
```
nostr_console.exe  --prikey=K
```

To get the latest messages for user with private key K for last 4 days ( default is 1) from relay R: 
 
```
nostr_console.exe  --prikey=K --relay=R --days=4 
```

 To write events to a file ( and later read from it too), for any given private key K:

```
nostr_console.exe  --file=eventsFile.txt --prikey=K
```

 
 # Screenshots

![As of](https://pbs.twimg.com/media/FachGW3agAAele4?format=png&name=4096x4096) mid Aug 2022.

![Showing Tree with re-shifting to left](https://pbs.twimg.com/media/Fao3E1bUUAAIti1?format=png&name=4096x4096) showing re-alignment of threads for easier reading.






 
