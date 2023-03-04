import logging
import os
import requests
import time

logging.basicConfig(filename='api.log', level=logging.INFO,
                    format='%(asctime)s - %(levelname)s - %(message)s')

# Read API endpoints from a configuration file or environment variable
API_ENDPOINTS = os.environ.get('API_ENDPOINTS', '').split(';')

# Define maximum retries and retry interval
MAX_RETRIES = 3
RETRY_INTERVAL = 5  # seconds

# Define supported HTTP methods
HTTP_METHODS = ['GET', 'POST', 'PUT', 'DELETE']

# Define rate limiting parameters
RATE_LIMIT = 10  # requests per minute
LAST_REQUEST_TIME = 0

def make_request(method, url, data):
    global LAST_REQUEST_TIME

    # Validate HTTP method
    if method.upper() not in HTTP_METHODS:
        logging.error(f'Invalid HTTP method {method}')
        return

    # Implement rate limiting
    current_time = time.time()
    if current_time - LAST_REQUEST_TIME < 60 / RATE_LIMIT:
        time.sleep(60 / RATE_LIMIT - (current_time - LAST_REQUEST_TIME))
    LAST_REQUEST_TIME = time.time()

    # Implement retries
    for i in range(MAX_RETRIES):
        try:
            response = requests.request(method, url, data=data)
            response.raise_for_status()
            logging.info(f'{method} request to {url} succeeded with response {response.text}')
            break
        except requests.exceptions.HTTPError as e:
            logging.error(f'{method} request to {url} failed with status code {e.response.status_code}')
            break
        except requests.exceptions.RequestException as e:
            logging.warning(f'{method} request to {url} failed with error {e}')
            if i < MAX_RETRIES - 1:
                time.sleep(RETRY_INTERVAL)

# Iterate through API endpoints and make requests
for endpoint in API_ENDPOINTS:
    data = {'key': 'value'}
    make_request('POST', endpoint, data)
