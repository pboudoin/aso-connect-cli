# ASO + Connect

ASO + Connect is a command line tool to help you optimize your app store metadata and get insights from your app store connect account.
It is built on top of the App Store Connect API and the Apple Search Ads API.
With ASO + Connect, you can:
- Get the ranking of your app for a specific keyword and country
- Extract keywords from the top apps in the store for a specific search term
- Get the popularity of a keyword
- Update your app metadata in App Store Connect (bye-bye manual updates)
- Translate automatically your app metadata into all languages supported by the App Store
- Get reviews from your app
- Get a marketing analysis of your app based on the reviews
- Search within the AppStore in command line

## How to use

### Install
1. Create a virtual environment
```bash
conda create -n aso python=3.10
conda activate aso
```
2. Install the required packages
```bash
pip install -r requirements.txt
```
3. Get keys and Certificates from App Store Connect and Apple Search Ads
4. Create a `.env` file with the following content:
```bash
OPENAI_API_KEY=your_key_id
```

### List your apps
List all of your apps in App Store Connect
```bash
python connect.py
```

### Update app metadata in App Store Connect

Update all metadata for all languages from the french version of the app with the id 1198765923

```bash
python connect.py release_notes -i 1198765923 -l fr-FR
```

If you want to update only the release notes of a specific version, you can use the following command:
```bash
python connect.py release_notes -i 1198765923 -l fr-FR -f whatsNew
```

### Keywords identification and optimization (ASO)

Extract all keywords from the top 20 apps in the French store for the keyword "medicament"
```bash
python connect.py optimize_metadata -i 1462935634 -l fr-FR -n 25 -s "medicament"
```

Get the keyword popularity for the keyword "scores"
```bash
python connect.py search_keywords --search "scores"
```

Get the keywords popularity for the keywords "nounou;assistante maternelle;assmat"
```bash
python connect.py search_keywords --search "nounou;assistante maternelle;assmat"
```

### Get reviews
```bash
python connect.py reviews -i 6450518012
```


### Get Rankings
Get the ranking of the app with the id 1670557657 in the French store for the keyword "assmat"
```bash
python connect.py ranking -i 1670557657 -l fr-FR -n 25 -s "assmat"
```
