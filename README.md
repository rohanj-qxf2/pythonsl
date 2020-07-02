# pythonsl
A python client for running tests in sauce labs

# About
This package aims to provide a straighforward python client to interact with sauce labs

  
# Pre-requisites
* pythonbs requires [Python3](https://www.python.org/download/releases/3.0/)  to run
* selenium installed  if not ```pip3 install selenium```


### Installation

This client is hosted at PyPi under the name pythonsl, to install it, simply run
```
pip install pythonsl
```
# Examples
```
import pythonsl as sl
from selenium import webdriver

def test_sl():
    try :
        capabilities = {
            'browserName': 'chrome',
            'browserVersion': '70.0',
            'platformName': 'Windows 10'
        }
        username = ''
        accesskey = ''
        driver = sl.get_webdriver(username,accesskey,capabilities)
        driver.get("http://www.google.com")
        if not "Google" in driver.title:
            raise Exception("Unable to load google page!")
        elem = driver.find_element_by_name("q")
        elem.send_keys("BrowserStack")
        elem.submit()
        print(driver.title)
        driver.quit()
    except:
        driver.close()
        driver.quit()
    

if __name__ == "__main__":
    test_sl()

```


Obtain your username and accesskey values from sauce labs user settings and Update the values of variable names username & accesskey 
Run your file and you will see your script run in sauce labs 

You can change the desired capabilities by referring to - https://wiki.saucelabs.com/display/DOCS/Platform+Configurator#/
