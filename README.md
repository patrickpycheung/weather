# Weather API Application

  Table of contents

  * [**Version history**](#version-history)
  * [**About the application**](#about-the-application)
  * [**Operation manual**](#operation-manual)
    * [**Pre-requsites**](#pre-requsites)
    * [**Steps**](#steps)
    * [**Reference**](#reference)

## **Version history**

  | Version| Date | Description | 
  | --- | --- | --- | 
  | 1.0.0 | 1 Feb 2021 | Initial release |

## **About the application**

The Weather application is a RESTful API implementation which retrieves weather information of a city. It also retrieves the list of cities of a country. It exposes the functions of the GlobalWeather web service (actual WSDL at http://www.webservicex.com/globalweather.asmx?WSDL, but the service is not available at the time of development, hence a local node.js application is used to mock the reponses). 

The API gets the request parameters from the user, and calls the GlobalWeather web service for the query. It organizes the returned  raw data, then gives the organized response to the user.

## **Operation manual**

  ### Pre-requsites

  * AnyPoint Studio 7.7 (Use Maven 4.3.0 to run the application)
  * Maven 4.3.0 standalone runtime (if you would like to run the application independently)
  * Maven
  * JDK8
  * An API testing tool (e.g. Postman)
  ### Steps

  Note: The following assumes you are running the setup locally in your machine

  1. Start up the GlobalWeather Web Service node.js simulation application
  2. Clone the Weather API source (main branch)
    
    git clone https://github.com/patrickpycheung/weather.git

  3. Run the Weather API application

        **Run the application within AnyPoint Studio**
        
      a. Import the project into AnyPoint Studio 
        <br/>
        <br/>
        <img src="https://bn1301files.storage.live.com/y4mbsi5YjqIcax3KmJ-JvaNezgtO5iClZE5OFCDNc1LlNIKaPk8rMBXQvj0wlnBzviZef5Wmzr1V6S712zklMl_EIZbMq7utzPbRu44jCIwdwmKDwwd6ZxVFKtb90onsrhj74e-PioUX-8NSZHToU_cfU0XqPd40AmEAb13lZodgpJ7Zz7EOQWz6JsxewMImZ_G?width=5108&height=2748&cropmode=none" title="Import_project_to_Anypoint_Studio_01" alt="Import_project_to_Anypoint_Studio_01">

        <img src="https://bn1301files.storage.live.com/y4mS3tBHxcthD0VKNinSeGGOzJrgdJzME5nT_y3Y_b7GBEnoOn_C0IKYrUqZyXKj5NDi3xoShWoa-sRiCBg3BbqFNgHNCHgXeH07MROYlRzcFDH7q8l-fo_0syQlFYYtLOaGryBFlkMbFVg4ZxylnhlpCn4HIWiq1oLtwFawAkOq22HnBTGLaXe8II5fqQ0pK-0?width=1642&height=1102&cropmode=none" title="Import_project_to_Anypoint_Studio_02" alt="Import_project_to_Anypoint_Studio_02">
        <br/>
        <br/>
      b. Configure the run setting for the project
        <br/>
        <br/>
        <img src="https://bn1301files.storage.live.com/y4mVFnw2zPa99leO4o9tfzndEnp835oP1gd84ijCWC55AWd1sE1_gzl4KwuFAXP4SJp3T74BBu7MEIRtzy_MloCnTrjZpuUlz6gPBnVHolHOQMk4_P43F_k_I3QQPUEXa7igbdb2muviz9-R6YP7M_EZ16L0OQAgJbUNEUwrUQIPwvcNGi7UhDoFdp5EmuExsrQ?width=1776&height=1702&cropmode=none" title="Run_configuration_01" alt="Run_configuration_01">

        <img src="https://bn1301files.storage.live.com/y4mikOtY78hdQobJQXeK7BPJ-Ga03qiQ4GDot6RAyScBVONYWGaz7djaQoVvYpdFVz_PP0mr_NOLDrWiia7XG5MypAOY4gLVwq3zxT8-l2n-aj71RslNrvnPZEMJQG5V5-0yKwQJNYQyrCDqxHJKObePQOupBgKqlU7KGjp3e6WCauCVSLmcQPxOFx-wXc1VleV?width=3260&height=2830&cropmode=none" title="Run_configuration_02" alt="Run_configuration_02">
        <br/>
        <br/>
        Set a JVM argument to specify the log level.
        <br/>
        <br/>
        <img src="https://bn1301files.storage.live.com/y4mKzVfUj2pWkYB3YAoJxNveXcES0peTU8oKL9loF3m25ZH70hMTIbAp7rOi7429eQyIC1IuzpgEOHPz0MVISEymOM9mxgHC72jT0z2MgEm1_YzKXJOIQghDlvI9mWAY_pVCYUJMvBtmkIG4lAVxMjE4zrl6CgrsjQcU20qznjVET3rr--jkSR2FDlTaLuL97VZ?width=2308&height=2856&cropmode=none" title="Run_configuration_03" alt="Run_configuration_03">
        <br/>
        <br/>
      c. Launch the application
        <br/>
        <br/>
        <img src="https://bn1301files.storage.live.com/y4mOQXhYSI8zcl6dGnIjaPorrHDgFYeC8gDV_A8zdxaucaUHPj4V3hvzPfwE6hz8n6WRxALz-AjuBRBVT3Cwfv2gykJREAO5pV2C3aJSc2e_4Y_ppi2NcHdxNfESvR2UzHNPXs0OOTjLtzUNTsZ4pRX5HM_lDQXS4omOdI8mj__2v3TtfhxPqmvKP-6JWMRZUEW?width=1616&height=1734&cropmode=none" title="Anypoint_studio_launch_application_01" alt="Anypoint_studio_launch_application_01">

        <img src="https://bn1301files.storage.live.com/y4mBw04NiWIC9j1etMcnjEJVhtf1_8R0pBgR1iAO1uCEbdIwCaUmcSQBNMKiWQcc36DjqeZw2vZXD0AXH8wuzMuIAjirOhCo61kTHMK7uBZImBeSEeetvYLrvXBe2n5Y6aW642FpBM5xmK8ejkvfx66MSqooXwYYTeXIQLyJrOQRLJSd-7K8roSpBURMO65hNG8?width=2012&height=718&cropmode=none" title="Anypoint_studio_launch_application_02" alt="Anypoint_studio_launch_application_02">

        **Run the application with standalone Mule runtime**

      * Build the application JAR file
      
        Go to the root folder of the application source. Execute the following maven commands to build the JAR file.

    mvn clean package -DskipMunitTests

<br/>
        <img src="https://bn1301files.storage.live.com/y4migUjq3-JLywJxm9ZLXAajSXoeNsD6LZawkB_Cv2n98dgZM4lPjg_9HPa8knRQdrzqQq7rqDIYapyCgRjdUXTG1G9Z-DFCKPI3m8_QCg_ORLQ4rogskn1P5rGENGiIo83ihxJ53B6vkRpRcPJhRo0Y8VV4hm9UfsHXCJ11w_6XlzjgkLtvNZJKvLXfEPGgLFM?width=2082&height=540&cropmode=none" title="Maven_build_01" alt="Maven_build_01">
        <br/>
        <img src="https://bn1301files.storage.live.com/y4m7iS8gcuRF01Bx8UguciNV-pPQdXk1XNPnIIs-1XIjTYkOw3HezNb-k_2jeaCav--HzOONkVdErz979HmElZgQ18pz8zPyMmbej8jf6E13g4DQDvrryVjaBK99fXzH9hVCRq61NPj97AyD-xhe9YEAgRPaHB_lXG5ztyVfhPP2JurKJYK1vk2LG7u4gtmen0c?width=2982&height=422&cropmode=none" title="Maven_build_02" alt="Maven_build_02">

<br/>
        (Note:<br/>
        At the time of preparing this document, there is an issue preventing casual users from including the Munit test phase in the Maven build. It requires enterprise license credentials to be present in the Maven settings file. 
<br/>
<br/>
        To run the Munit test case, you can execute them from within AnyPoint Studio.
<br/>
<br/>
        This should not be an issue for Enterprise users.
        
  Refer to [**Issue with running Munit in Maven test phase**](#issue-with-running-munit-in-maven-test-phase).)
<br/>
<br/>
<br/>
        The resulting JAR file will be located in the target folder.
        <br/>
        <br/>
        <img src="https://bn1301files.storage.live.com/y4mgZ9aQCPEbP6hzzUz0U8gvETXIf2Anzfm4MX1cUFC3soYOyCqOJVB8woj9J5xPQ1UDURo_hv8I1sxqNwq4bUHmvL7z1mmrgfwX8VewWpWwrrfuWLzyLmqP5ZiKqewZESD4TQjUZYcjd8Qq6xlNATOpnMbZA5GACF5WIzRaQa5lMHX8mocs_Pi8jTOsp3YDXDX?width=1468&height=440&cropmode=none" title="JAR_file_location" alt="JAR_file_location">
        <br/>

* Deploy the JAR file to the standalone Mule runtime
   * Get a copy of the Mule 4 standalone runtime.
      <br/>
      <br/>
   You may get it at https://www.mulesoft.com/lp/dl/mule-esb-enterprise
      <br/>
      <br/>
   * Copy the JAR file to the {mule-standalone-runtime}/apps folder
      <br/>
      <br/>
      <img src="https://bn1301files.storage.live.com/y4m8aYCDncDCbIu2_sTchDEDeombWda6dnJb5D_Pzg3eoPqcFcEppwFFLfMOeW8E_7D3g83y4UhrzoGdDR9wguT8qrGE8Ho63v5FPVShj-9uCCLj963MexHEb-JW4IsYogGig3MyqTP8WihVGUF5-_yLJH6xqmrtJ7T8Figuvh1Ef7P3vdbuSY9GtW_so-SARla?width=1692&height=692&cropmode=none" title="Copy_JAR_to_mule_standalone_runtime" alt="Copy_JAR_to_mule_standalone_runtime">
      <br/>
      <br/>
   * Go to the binaries folder {mule-standalone-runtime}/bin
    <br/>
    <br/>
      <img src="https://bn1301files.storage.live.com/y4m1pUajqdwbuZv3B7MLqstkTe_QfaZItlVwczdRlc5nNFLWH0nGjzAzSE-Z1c5ZLHlgpwDyg7cffRNk9wqGC1pdmiizDlwcF-bD1-FVsy8XdpuS5_Z5sdJQX1_I9-1tMeC7gYCPsDwkTca0chpj-VALean6NpXEC_6gNa3WSLEJLTPCJ3l1dXu6ajGLTEQFwEd?width=1484&height=692&cropmode=none" title="Go_to_mule_runtime_binary_folder" alt="Go_to_mule_runtime_binary_folder">
      <br/>
      <br/>
   Start up the server by the following command
    <br/>
    <br/>
      Linux/Unix/MacOS

            ./mule -Dlog.level=INFO
    <br/>
    <br/>
      Windows

            ./mule.bat -Dlog.level=INFO
    <br/>
    <br/>
      <img src="https://bn1301files.storage.live.com/y4me6MsG83CaifBIHMH6wONEFIpTsJe1MZAciMxmZvUICLU-9pJtvOBrM3HRBQpJCG3jnEbV8lYwNTaUQu3j9dRxDJVoIOmmUyUWEzXFpV98LqVk6l9SXCiSi7YgCg7w6wi_I7zH1sEF3z31z3vybizRf42glHrg6fRgJpKrhcX6V8VHXqaWXa2aGPoLawOzNgd?width=5102&height=2864&cropmode=none" title="Mule_standalone_runtime_launch_application_01" alt="Mule_standalone_runtime_launch_application_01">
      <br/>
      <img src="https://bn1301files.storage.live.com/y4myPjUuTSSJNjB_pFpcGfj7K9NE_4E-KkaIsXbZB3y-nZfnG-6uM_AnfXSDvzEY1fHBnhfPMNgIKC_H3PwgiTSW1RI5ST4drWBo_AebZh4fQXJd9UOqBrFSo_bW3bROP7spKLOXUuaSWviaSCfG89DHWn6Vq1joTtWujsaES0qKjkJvR117PRG1q3suYDCcMDZ?width=5102&height=2864&cropmode=none" title="Mule_standalone_runtime_launch_application_02" alt="Mule_standalone_runtime_launch_application_02">

   4. To supply additional configuration settings or override existing ones (e.g. to change the log level), add a JVM parameter on the mule command
   
   e.g.
  
      ./mule -M-Dlog.level=DEBUG

   5. Test the functioning of the application with some requests
    <br/>
    <br/>
  GET /cities
      <br/>
      <br/>
      <img src="https://bn1301files.storage.live.com/y4mu38NO90LmVB8QWap-SOEBxLwmoWQykL7Uw68Ax5DM78KXfUXk3iHFEwA4kK-jag-DB_4ckWl7OiIyHYs21jMLVTzYZRIW4YGUtOmEpWY9ifTIn8SUUuWHIuhe63t4wvOLaZL42wXbOr6U4UquXGnuwyvNuPlq-6-_j18lie2I5jDuorIWNNjtfIzbNCXvyAA?width=4524&height=2548&cropmode=none" title="Test_get_cities" alt="Test_get_cities">
      <br/>
  GET /weather
      <br/>
      <br/>
      <img src="https://bn1301files.storage.live.com/y4mdk-VFFGfc7AHC_XEaViCrPmbwPSxVL-XoajlervaMzatDImlovElGbyEfG8SQIokMvQeRtRFLGuMznKJNVsGuKOCWB0oojsIsY-NJmKhpKypLmzG3iHiS6Y0lye7F3fDpffmYC4BkYNLT2GZNHaht39rAiFw2YmZSNTab2FnHtgEtb8m96HmOx90yP45dWE1?width=4524&height=896&cropmode=none" title="Test_get_weather" alt="Test_get_weather">

   6. You may deploy the application to CloudHub , but you will have to use the actual GlobalWeather web service endpoint.
   <br/>
   Or you may deploy the node.js containerized application to somewhere accessible with a reachable URL.
   <br/>
  Either case, you will have to update and override the GlobalWeather web service configuration values.
   <br/>
   <br/>

  <img src="https://bn1301files.storage.live.com/y4meMYOMGOCvXk0mUFzwtLuomrFg8L93gdYHAeXvBFxm2jdXy1WO-CooMNnQ7n9WmhLlcgnDLlH0d8bZPPO_Ru5_P5I9FxeoA4ObasBRDsTcB5S0ArD3G45C-v1k6tm5ZIes8skSDzONT6h0pRK-g6xhZcYSkwytDPxjtc8ZCt1GZsb0YiTRP_XmAU7sLf-Vwv7?width=866&height=180&cropmode=none" title="Config_for_GlobalWeather_web_service" alt="Config_for_GlobalWeather_web_service">

## **Reference**

### **Issue with running Munit in Maven test phase**
https://help.mulesoft.com/s/question/0D52T00004mXXkv/unable-to-run-munits-after-upgrading-mule-runtime-to-420-from-413-details-of-the-error-is-prov

### **Mule 4 standalone runtime download site**
https://www.mulesoft.com/lp/dl/mule-esb-enterprise